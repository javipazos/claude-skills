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

Use when reflecting, evaluating a decision, or seeking perspective. Activates 2-3 relevant thinkers based on your situation and uses the Socratic method to help you think through problems.

### persuade

Use when creating something meant to influence -- web pages, documents, presentations, or preparing conversations. Applies the combined frameworks as actionable checklists with context-specific references for web design, documents, and conversations.

### sinek

Deep dive into Simon Sinek's frameworks specifically: Golden Circle, Circle of Safety, Infinite Game, Celery Test.

### sutherland

Deep dive into Rory Sutherland's frameworks specifically: psycho-logic, psychological moonshots, reframing, costly signals, satisficing.

### pink

Deep dive into Daniel Pink's frameworks specifically: autonomy/mastery/purpose, timing science, the four regrets, the ABCs of selling.

### kahneman

Deep dive into Daniel Kahneman's frameworks specifically: System 1/2, prospect theory, heuristics and biases, noise, WYSIATI.

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
