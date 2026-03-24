# Skill.md Archive

A growing collection of Skill.md files for [Claude Code](https://claude.ai/claude-code) — gathered from real usage across different projects and AI tools.

## What are Skill.md files?

Skills are custom slash commands for Claude Code. Drop a `.md` file into `~/.claude/skills/` and invoke it with `/skill-name` directly in your Claude Code session.

Each file in this repo is a ready-to-use skill.

## How to use a skill

1. Copy the skill file you want to `~/.claude/skills/`:
   ```bash
   cp commit.md ~/.claude/skills/
   cp skill.md ~/.claude/skills/
   ```
2. In Claude Code, invoke it by its filename (without `.md`):
   ```
   /commit
   /skill
   ```

That's it.

## Skills

| Name | File | Description |
|------|------|-------------|
| commit | [commit.md](commit.md) | Stage, write, and create a well-formatted git commit |
| skill | [skill.md](skill.md) | Load Robinhood Chain Testnet context (network params, contracts, deploy steps) into Claude before building on-chain |

## Adding a new skill

1. Create a new `.md` file at the root of this repo
2. Add a row to the table above
3. Open a PR or push directly if you're the maintainer
