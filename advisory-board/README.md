# Advisory Board

A Claude Code plugin that gives you access to an advisory board of five thinkers for reflection, decision-making, and persuasion.

## The Five Perspectives

- **Simon Sinek** -- Purpose, leadership, the Golden Circle, the Infinite Game
- **Rory Sutherland** -- Perception, reframing, behavioral economics, psycho-logic
- **Daniel Pink** -- Motivation, timing, regret, persuasion
- **Daniel Kahneman** -- Cognitive biases, decision quality, prospect theory, noise
- **Stoic Philosophy** -- Emotional regulation, virtue, dichotomy of control (Marcus Aurelius, Seneca, Epictetus)

## Skills

### think

Use when reflecting on a non-code decision (career, relationships, team dynamics, life choices, business direction). Activates 2-3 relevant thinkers based on your situation and uses the Socratic method to help you think through problems.

### persuade

Use when crafting persuasive content — the narrative of a landing page, the argument of a proposal, a sales email opening, or the framing of a difficult conversation. Applies the combined frameworks as actionable checklists.

## Accessing Individual Thinkers

The four author lenses (Sinek, Sutherland, Pink, Kahneman) and Stoic philosophy live as reference files inside the `think` skill and are loaded automatically based on your situation. If you want to consult a single thinker directly, invoke `/advisory-board:think` and request that lens by name (e.g. "apply only the Sinek lens").

## Installation

Add to your Claude Code plugins configuration:

```json
{
  "advisory-board": {
    "type": "git",
    "url": "https://github.com/javipazos/claude-skills",
    "directory": "advisory-board"
  }
}
```

## Claude Desktop

The `think` skill includes a `claude-desktop-project-knowledge.md` reference file that can be copied into a Claude Desktop Project as "Project Knowledge" to have these frameworks available in Desktop conversations.
