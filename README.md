# eli5

Two writing skills for AI agents:

- `eli5` explains things in plain, concise English for a busy executive.
- `asd-ste100` writes technical content in ASD-STE100 Simplified Technical English (STE).

Works in both Claude Code and OpenAI Codex CLI. Both tools use the same skill format, so this repo holds both skill definitions and two install paths.

## What it does

### eli5

When you write "eli5" in a prompt, or ask for a plain-English version, the agent gives you the bottom line in short, natural language.

It applies to anything: agent responses, specs, docs, plans, bug reports, code review comments.

### asd-ste100

When you write "ASD-STE100" or ask for Simplified Technical English, the agent uses the STE writing rules and controlled dictionary.

- It uses approved words with their approved meanings and parts of speech.
- It applies the separate STE rules for procedures, descriptions, and safety instructions.
- It preserves code, commands, identifiers, and other text that must stay unchanged.

The skill targets ASD-STE100 Issue 9, dated January 15, 2025. The official standard is available from [asd-ste100.org](https://www.asd-ste100.org/).

## Install in Claude Code (plugin, recommended)

This repo is a Claude Code plugin marketplace containing one plugin.

From GitHub:

```
/plugin marketplace add rahulj51/eli5
/plugin install eli5@eli5
```

From a local clone:

```
git clone https://github.com/rahulj51/eli5.git
```

Then in Claude Code:

```
/plugin marketplace add /path/to/eli5
/plugin install eli5@eli5
```

Then use either skill:

- `/eli5 <paste text or describe what to simplify>`
- `/asd-ste100 <paste technical text or describe what to write>`
- Or include "eli5" or "ASD-STE100" in a natural prompt. The matching skill triggers automatically.

To update later: `/plugin marketplace update eli5`.

## Install in Codex CLI

Codex uses the same Agent Skills format. The easiest way is the `skills` CLI from [skills.sh](https://www.skills.sh), which pulls the skill from GitHub and installs it into the right directory:

```
npx skills add rahulj51/eli5 -a codex
```

The command lets you select one or both skills. Add `-g` to install globally and `-y` to skip prompts. This command installs both:

```
npx skills add rahulj51/eli5 -a codex -s eli5 -s asd-ste100 -g -y
```

The same command works for other agents too. Run it without `-a` and it detects every agent you have installed (Claude Code, Codex, Cursor, and others) and asks where to install.

Manual alternative, if you have this repo cloned locally:

```
mkdir -p ~/.codex/skills
ln -s /path/to/eli5/skills/eli5 ~/.codex/skills/eli5
ln -s /path/to/eli5/skills/asd-ste100 ~/.codex/skills/asd-ste100
```

Codex loads skills automatically when a request matches a skill's description. To update after a skill change, re-run the npx command. A symlink updates by itself.

## Repo layout

```
.claude-plugin/marketplace.json   Claude Code marketplace manifest
.claude-plugin/plugin.json        Claude Code plugin manifest
skills/eli5/SKILL.md              The skill itself (shared by Claude and Codex)
skills/asd-ste100/SKILL.md        The ASD-STE100 skill (shared by Claude and Codex)
skills/asd-ste100/agents/         Codex UI metadata for the ASD-STE100 skill
```

## Editing the skill

Behavior lives in each skill's `SKILL.md`. Edit it, push, and reinstall or update in each tool.

## License

MIT. See [LICENSE](LICENSE).
