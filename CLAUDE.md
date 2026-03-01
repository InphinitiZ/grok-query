# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

An [OpenClaw](https://openclaw.ai) skill that enables AI agents to query Grok AI (grok.com) for real-time information via browser automation. The skill is a single `SKILL.md` file following the OpenClaw skill spec, intended for publication on [clawhub.ai](https://clawhub.ai).

## Skill File Format

`SKILL.md` uses YAML frontmatter followed by Markdown content. Supported frontmatter fields:
- `name`, `description`, `license`, `metadata` (required/common)
- `argument-hint`, `compatibility`, `disable-model-invocation`, `user-invokable` (optional)
- **Not supported**: `homepage` (will cause linter warnings)

The `metadata.openclaw` block can include `emoji`, `requires.bins`, and `install` arrays.

## Key Constraints Discovered During Testing

- **Grok uses Enter for newline, not send** — must click the "Submit" button (⬆ icon)
- **Input box is a ProseMirror `contenteditable` div**, not a standard `<textarea>` — shows as `paragraph` in snapshots
- **Browser tool calls have a ~20s timeout** — `wait --text-gone` or `wait --fn` with long timeouts will fail; use `wait --time 10000` + `snapshot` polling loop instead
- **Element refs change between interactions** — always re-snapshot before typing or clicking
- **"Upgrade to SuperGrok" banner** frequently obstructs the page — handle in workflow

## Deployment

Copy to OpenClaw workspace for local use:
```bash
cp SKILL.md ~/.openclaw/workspace/skills/grok-query/SKILL.md
```

## Linting

Open `SKILL.md` in VS Code with the OpenClaw extension to see diagnostics for unsupported frontmatter fields or formatting issues.
