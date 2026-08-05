# eli5

A skill that makes AI agents use ASD-STE100 Simplified Technical English (STE). STE is a controlled form of English for clear and accurate technical writing.

Works in both Claude Code and OpenAI Codex CLI. Both tools use the same skill format (a folder with a `SKILL.md` file), so this repo holds one skill definition and two install paths.

## What it does

When you write "eli5" in a prompt, or ask for a plain-English version of something, the agent rewrites the content with ASD-STE100 only.

- It uses the STE writing rules and controlled dictionary.
- It uses approved words with their approved meanings and parts of speech.
- It treats subject terms as technical nouns or technical verbs.
- It uses short sentences, controlled verb forms, and the active voice.
- It applies the separate STE rules for procedures, descriptions, and safety instructions.
- It preserves code, commands, identifiers, and other text that must stay unchanged.

It applies to anything: agent responses, specs, docs, plans, bug reports, code review comments.

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

Then use it either way:

- Explicitly: `/eli5 <paste text or describe what to simplify>`
- Naturally: just include "eli5" in any prompt, e.g. "eli5 this bug report". The skill's description triggers automatically.

To update later: `/plugin marketplace update eli5`.

## Install in Codex CLI

Codex uses the same Agent Skills format. The easiest way is the `skills` CLI from [skills.sh](https://www.skills.sh), which pulls the skill from GitHub and installs it into the right directory:

```
npx skills add rahulj51/eli5 -a codex
```

Add `-g` to install globally (all projects) instead of just the current project, and `-y` to skip prompts:

```
npx skills add rahulj51/eli5 -a codex -g -y
```

The same command works for other agents too. Run it without `-a` and it detects every agent you have installed (Claude Code, Codex, Cursor, and others) and asks where to install.

Manual alternative, if you have this repo cloned locally:

```
mkdir -p ~/.codex/skills
ln -s /path/to/eli5/skills/eli5 ~/.codex/skills/eli5
```

Codex loads skills automatically when a request matches the skill's description, so saying "eli5 this" in a prompt is enough. To update after a skill change, re-run the npx command (a symlink updates by itself).

## Repo layout

```
.claude-plugin/marketplace.json   Claude Code marketplace manifest
.claude-plugin/plugin.json        Claude Code plugin manifest
skills/eli5/SKILL.md              The skill itself (shared by Claude and Codex)
```

## Editing the skill

All behavior lives in `skills/eli5/SKILL.md`. Edit it, push, and reinstall or update in each tool.

## License

MIT. See [LICENSE](LICENSE).
