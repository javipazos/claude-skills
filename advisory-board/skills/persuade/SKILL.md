---
name: persuade
description: Use when the user is creating something meant to influence or persuade — designing web pages, writing documents, preparing presentations, planning negotiations, or preparing for difficult conversations. Triggers on mentions of "landing page", "proposal", "pitch", "negotiate", "convince", "presentation", "persuade", or when creating content intended to move people to action.
---

# Persuade — Frameworks for Creation and Influence

Apply the combined teachings of Sinek, Sutherland, Pink, and Kahneman as actionable checklists when creating web pages, documents, presentations, or preparing conversations.

## How to Behave

1. Ask what the user is creating and who the audience is
2. Identify the output type: web page, document/presentation, or conversation
3. Load the appropriate context-specific reference file
4. Apply frameworks as a concrete checklist — not philosophy, but specific instructions
5. Challenge weak choices by referencing specific principles
6. When reviewing existing work, flag where frameworks are violated and suggest specific fixes

## Output Type Detection

Determine which reference to load based on what the user is doing:

- **Web pages, landing pages, interfaces** → Load [references/web-design.md](references/web-design.md) for the web-specific checklist
- **Documents, proposals, presentations, pitch decks** → Load [references/documents.md](references/documents.md) for the document-specific checklist
- **Conversations, difficult talks** → Load [references/conversations.md](references/conversations.md) for the interpersonal checklist
- **Bidirectional negotiations** (salary, contracts, vendor terms, counter-offers) → Suggest using `/negotiate` instead — it provides a specialized three-phase workflow (Prepare → Draft → Review) with evidence-based techniques for written negotiation

If multiple apply (e.g., a proposal that will also be presented in person), load both.

## Quick Checklist (All Contexts)

Before the user finalizes anything, verify:

- [ ] **Starts with WHY** — belief/purpose before features/details (Sinek)
- [ ] **Loss frame considered** — what the audience loses by not acting (Kahneman)
- [ ] **Reframe tested** — is there a better way to frame the question? (Sutherland)
- [ ] **Audience perspective modeled** — what does THEIR world look like? (Pink: attunement)
- [ ] **Costly signal present** — something that shows genuine investment (Sutherland)
- [ ] **Ending engineered** — the last thing they see/hear/read is deliberately designed (Kahneman: peak-end rule)
- [ ] **Ethical check** — will their life genuinely improve if they agree? (Pink)

## Author Reference Files

Load these only when the user needs deeper detail on a specific author's approach — not as default. The context-specific references above are the primary resources.
- [references/sinek.md](references/sinek.md) — leadership, purpose, WHY
- [references/sutherland.md](references/sutherland.md) — perception, reframing, psycho-logic
- [references/pink.md](references/pink.md) — motivation, timing, persuasion
- [references/kahneman.md](references/kahneman.md) — biases, decision quality, framing
