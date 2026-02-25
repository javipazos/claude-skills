---
name: terraform-upgrade
description: Guide Terraform version upgrades from 0.11 through latest with automated fixes, recommended tools, and developer guidance
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebFetch, WebSearch, AskUserQuestion
argument-hint: [current-version target-version]
metadata:
  author: jpazos
  version: "2.0.0"
---

# Terraform Version Upgrade Skill

Upgrade Terraform configuration files between versions using official tools, automated fixes, and safe state management.

## SAFETY GUARANTEE — Communicate This First

Before doing anything else, tell the developer:

> **This skill will NEVER run `terraform apply`.** No infrastructure changes will be made.
>
> I will only modify Terraform configuration files (.tf), run upgrade tools (`terraform 0.12upgrade`, `terraform 0.13upgrade`), and use `terraform init`, `terraform validate`, `terraform plan`, and `terraform fmt` for verification.
>
> Your actual infrastructure remains untouched until you (or your CI pipeline) explicitly apply the changes.
>
> Before starting, I will back up your current Terraform state as a safety net.

**HARD RULE: The agent MUST NEVER run `terraform apply` unless the developer explicitly requests it AND confirms a second time when prompted.** If the developer asks to apply, respond:

> Are you sure you want to apply infrastructure changes? This will modify real resources. Please confirm with "yes, apply" to proceed.

Only proceed on explicit second confirmation.

## Phase 1: Gather Context

### Detect Current Version

Search the codebase in this order. Stop at the first match:

1. **Glob** for `.terraform-version` in project root — read the version string
2. **Grep** for `required_version` in `*.tf` files — parse the constraint
3. **Bash**: `terraform version` if the binary is available
4. If all fail, **AskUserQuestion** to get the current version

### Verify the Actual Version

The developer's stated version is a starting hint, not a fact. Always verify by running:

```bash
terraform version
terraform state pull 2>/dev/null | head -5
```

Check the `terraform_version` field in the state to see which version last wrote to it.

**If there is a mismatch** between config files (`required_version`), the installed binary, and the state version, inform the developer:

> I found a version mismatch:
> - Config files declare: `X.Y`
> - State was last written by: `X.Z`
> - Installed binary: `X.W`
>
> The state version is the hard constraint — the migration path must start from the oldest version to ensure state compatibility. Does this look right?

**Rule: The migration starting point is the OLDEST of (state version, declared version).** The state format is the hard constraint — you can't skip state format migrations regardless of what the `.tf` files say.

### Validate That Declared Versions Actually Exist

The `required_version` in config files may reference a version that was never released (e.g., "0.11.15" — the last 0.11.x was 0.11.14). This indicates the value was manually set and never validated against an actual binary.

Check the declared version against known Terraform release history. The valid latest patch versions for each 0.x minor series are:
- 0.11.x → 0.11.14
- 0.12.x → 0.12.31
- 0.13.x → 0.13.7
- 0.14.x → 0.14.11
- 0.15.x → 0.15.5

If the declared version doesn't exist, inform the developer and use the nearest valid version as the starting point.

### Detect Target Version

1. Parse from `$ARGUMENTS` (expects `current-version target-version` or just `target-version`)
2. If not provided, **WebSearch** for `"terraform latest stable release version"` to confirm current latest
3. Confirm the target with the developer

### Detect Platform

Run via **Bash**:
```
uname -m    # arm64 = Apple Silicon, x86_64 = Intel/AMD
uname -s    # Darwin = macOS, Linux = Linux
```

ARM64 native Terraform builds started at **v1.0.2**. If the platform is arm64 AND the migration path includes versions older than 1.0.2, the developer must choose a compatibility approach — see Phase 2.

## Phase 2: Choose Execution Preferences

Ask preferences **one at a time** using **AskUserQuestion**. Wait for each answer before asking the next. Skip questions that are irrelevant based on the detected context.

### Question 1: Execution Mode

> **How much control do you want over the upgrade process?**
>
> **A) Supervised (recommended)** — I upgrade one version at a time, show you results, and wait for your go-ahead before the next step. I only ask questions when there are genuine decisions (removed features, architectural choices).
>
> **B) Full auto** — I run through the entire upgrade path without stopping. I only pause if something fails (validation error, unexpected plan diff). Good for well-tested codebases.
>
> **C) Plan only** — I analyze your codebase and produce the full upgrade plan with all breaking changes and steps, but I don't touch any files. You execute manually.

### Question 2: Tool Installation

> **Should I install the required Terraform versions automatically, or do you want to approve each?**
>
> I need intermediate Terraform versions to run their upgrade commands. I use tfenv if available.
>
> **A) Auto-install** — I install each version as needed
> **B) Ask first** — I tell you which version I need and wait for your approval

### Question 3: ARM64 Compatibility

**Only ask if `uname -m` is `arm64` AND the migration path includes versions < 1.0.2.** Skip entirely otherwise.

> **Your system is ARM64, but Terraform versions before 1.0.2 don't have ARM64 builds.**
>
> **A) Rosetta 2 + tfenv (recommended, macOS only)** — Simplest approach. I install x86_64 binaries via `TFENV_ARCH=amd64 tfenv install X.Y.Z`. Rosetta 2 runs them transparently. No container overhead, direct filesystem access.
>
> **B) Docker** — I run old Terraform versions in a container with your project directory mounted. Works on both macOS and Linux ARM64, but adds complexity with volume mounts and credential forwarding.

If the developer picks Rosetta 2, verify it's available:
```bash
/usr/bin/pgrep -q oahd && echo "rosetta_installed" || echo "not_installed"
```
If not installed, instruct: `softwareupdate --install-rosetta --agree-to-license`

If on Linux ARM64, only option B (Docker) is available — inform the developer.

If the developer picks Docker, read `~/.claude/skills/terraform-upgrade/docker-credentials.md` for credential forwarding patterns. Ask the developer which backend they use (S3, GCS, AzureRM, Terraform Cloud, etc.) and follow the corresponding credential mounting instructions from that file.

### Permission Considerations

After collecting preferences, inform the developer about Claude Code's permission system:

**For Supervised mode:** Permission prompts are less disruptive since you're already reviewing each step. Approve tools as they come.

**For Full Auto mode:** Permission prompts will interrupt the automated flow. Recommend the developer accept with "Always allow" when first prompted for Bash, Edit, Read, and Grep tools so subsequent calls proceed without interruption.

## Phase 3: Calculate Migration Path

### Pre-Upgrade Baseline (CRITICAL)

**Always run `terraform plan` on the CURRENT version before starting any upgrade.** It must show no pending changes. Upgrading with pending changes mixes version migration with infrastructure drift, making failures much harder to diagnose.

If pending changes exist, inform the developer and recommend applying them first (or explicitly deciding to carry them through the upgrade).

### Sequential Upgrades for 0.x — WHY They Are Required

Each Terraform 0.x minor release changed the **state serialization format** and shipped a version-specific upgrade command available ONLY in that version's binary:

- `terraform 0.12checklist` — exists only in 0.11.14, previews what 0.12upgrade will do
- `terraform 0.12upgrade` — exists only in 0.12.x, removed in 0.13
- `terraform 0.13upgrade` — exists only in 0.13.x, removed in 0.14

These commands transform HCL syntax and migrate state in ways that **cannot be skipped**. A 0.12 state file is unreadable by 0.14 — it must pass through 0.13 first. **Skipping any version risks state corruption and data loss.**

### 1.x Versions Can Be Jumped

Since 1.0, the state format is **stable and forward-compatible** per the v1.0 Compatibility Promises. You can jump directly from any 1.x to any later 1.x.

The agent MUST still read all intermediate version files to check for breaking changes that affect the specific codebase (e.g., S3 backend restructuring in 1.6, removed backends in 1.3). These are consolidated into a single upgrade step.

### Path Construction

```
FROM 0.11: 0.11 → 0.12 → 0.13 → 0.14 → 0.15 → 1.0 → [target 1.x]
FROM 0.12: 0.12 → 0.13 → 0.14 → 0.15 → 1.0 → [target 1.x]
FROM 0.13: 0.13 → 0.14 → 0.15 → 1.0 → [target 1.x]
FROM 0.14: 0.14 → 0.15 → 1.0 → [target 1.x]
FROM 0.15: 0.15 → 1.0 → [target 1.x]
FROM 1.x:  [current 1.x] → [target 1.x]  (direct jump)
```

## Phase 4: Present the Upgrade Plan

Before touching any files, present the developer with:

1. **Safety reminder** — no `terraform apply` will be run, state is backed up
2. **The full migration path** — each stop and why it's required (or why a jump is safe)
3. **Breaking changes summary** per stop (read from version files)
4. **Automated fixes** the agent will apply at each stop
5. **Manual decisions** the developer will need to make
6. **Recommended tools** per step (terraform upgrade commands, fmt, validate)

For **Plan Only** mode, stop here. For other modes, wait for developer confirmation.

## Phase 5: Execute Migration

### Before Starting — State Backup

Always back up state first. This is non-negotiable:

```bash
terraform state pull > terraform-state-backup-v{CURRENT}-$(date +%Y%m%d-%H%M%S).tfstate
```

Tell the developer where the backup was saved.

### Command Style Rules

To avoid breaking Claude Code's "Always allow" permission matching:

- **Use non-interactive flags**: `terraform 0.12upgrade -yes .` (not `echo "yes" | terraform 0.12upgrade .`)
- **Use `-force` when needed**: `terraform 0.12upgrade -force -yes .` if the tool refuses because `required_version` looks like 0.12+
- **Avoid piping output** through `tail`, `head`, or other filters — these change the command string and prevent blanket permission grants
- **Keep commands clean and predictable** so the developer can grant permission once per tool

### Provider Pinning Strategy

During intermediate upgrade steps, modern provider versions may be incompatible with old Terraform versions (protocol mismatches, binary too large for Rosetta 2). When this happens:

1. **Pin providers to compatible versions** for the upgrade step (e.g., `aws = "~> 3.0"` for 0.12 compatibility)
2. **Document what was pinned** so it can be restored
3. **Restore desired provider versions** at the final step after reaching the target Terraform version

### Submodule Handling

Upgrade commands (`0.12upgrade`, `0.13upgrade`) must run on **each module directory separately**, not just the root. Scan for submodules:

```
Grep pattern: source\s*=\s*"\./  in *.tf files
```

Also check for directories containing their own `.tf` files that aren't referenced as modules.

### For Each 0.x Transition

Read the version file: `~/.claude/skills/terraform-upgrade/versions/{FROM}-to-{TO}.md`

1. **Install the target version binary**
   - Auto-install mode: install via tfenv (with `TFENV_ARCH=amd64` if ARM64 + Rosetta)
   - Ask-first mode: tell the developer which version to install and wait
   - Docker mode: pull and use the appropriate hashicorp/terraform image (see `~/.claude/skills/terraform-upgrade/docker-credentials.md` for credential mounting and command patterns)
2. **Run pre-upgrade checks** if the version file specifies them (e.g., `terraform 0.12checklist` on 0.11.14)
3. **Fix pre-init blockers** — some HCL1 syntax issues prevent `terraform init` from running. The version file lists these. Fix them BEFORE init.
4. **Run `terraform init`** — required before upgrade commands
5. **Run the version-specific upgrade command** if one exists:
   ```
   terraform 0.12upgrade -yes .        # only in 0.12.x
   terraform 0.13upgrade -yes .        # only in 0.13.x
   ```
6. **Run upgrade command on each submodule** separately
7. **Apply additional automated fixes** from the version file using Grep + Edit
8. **Run `terraform fmt`** to normalize formatting
9. **Run `terraform validate`** — must pass
10. **Run `terraform plan`** — verify no unexpected changes (DO NOT APPLY)
11. **Report results** to the developer
12. **Handle manual decisions** — if the version file lists manual steps, present them and wait for input
13. In **supervised mode**, wait for go-ahead before next version
14. In **full auto mode**, proceed unless something failed

### For the 1.x Jump

Read ALL intermediate version files between current 1.x and target 1.x.

1. **Install the target version only** (intermediates not needed for 1.x)
2. **Consolidate** all breaking changes, automated fixes, and manual steps from all intermediate versions
3. **Present the consolidated list** to the developer
4. **Apply all automated fixes** using Grep + Edit
5. **Run `terraform init -upgrade`**
6. **Run `terraform fmt`**
7. **Run `terraform validate`**
8. **Run `terraform plan`** — verify (DO NOT APPLY)
9. **Handle manual decisions** if any

## Phase 6: Finalize

After all migration steps complete:

1. **Update `required_version`** in the terraform block to the target version
2. **Update `.terraform-version`** if the file exists
3. **Ensure `.terraform.lock.hcl`** is present (exists from 0.14+)
4. **Restore provider version pins** if any were temporarily downgraded during migration
5. Run **`terraform init -upgrade`** to fetch the restored provider versions
6. Run final **`terraform fmt -check`** — should pass
7. Run final **`terraform plan`** — should show no unexpected changes (DO NOT APPLY)
8. Present a **summary** to the developer:
   - Versions traversed
   - Breaking changes addressed
   - Manual decisions made
   - Files modified
   - Provider pins that were temporarily changed and restored
   - State backup location
   - Reminder: run `terraform apply` when ready (or let CI handle it)

## Important Notes

- **NEVER run `terraform apply`** — see safety guarantee above
- **Provider upgrades are separate** — this skill handles Terraform core only. Provider pinning should be reviewed after core migration.
- **Modules with their own `required_version`** need independent upgrade consideration. Scan for these and flag them.
- **Remote state**: if using a remote backend (S3, GCS, etc.), ensure no one else is running operations during the migration
- For the latest changelog: https://github.com/hashicorp/terraform/blob/main/CHANGELOG.md
- For v1.x compatibility promises: https://developer.hashicorp.com/terraform/language/v1-compatibility-promises
