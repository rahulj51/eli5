# eli5

A skill that makes AI agents explain things in plain, concise English for a busy executive (think CTO/CPO). Not a literal five-year-old explanation: simple words, short sentences, single-level lists with one or two sentences per item, bottom line first.

Works in both Claude Code and OpenAI Codex CLI. Both tools use the same skill format (a folder with a `SKILL.md` file), so this repo holds one skill definition and two install paths.

## What it does

When you write "eli5" in a prompt, or ask for a plain-English version of something, the agent rewrites the content following these rules:

- Plain, simple English with short, common words.
- Concise: every word earns its place.
- Bottom line first.
- Lists are single level only, one or two short sentences per item.
- Jargon is avoided or explained in a few plain words.
- Accurate: simple never becomes wrong.

It applies to anything: agent responses, specs, docs, plans, bug reports, code review comments.

## Install in Claude Code (plugin, recommended)

This repo is a Claude Code plugin marketplace containing one plugin.

From GitHub:

```
/plugin marketplace add rahulj51/eli5
/plugin install eli5@eli5
```

From the local folder (no GitHub needed):

```
/plugin marketplace add /Users/rahuljain/work/eli5
/plugin install eli5@eli5
```

Then use it either way:

- Explicitly: `/eli5 <paste text or describe what to simplify>`
- Naturally: just include "eli5" in any prompt, e.g. "eli5 this bug report". The skill's description triggers automatically.

To update later: `/plugin marketplace update eli5`.

## Install in Codex CLI

Codex uses the same Agent Skills format. Copy or symlink the skill folder into your Codex skills directory.

Personal (all projects):

```
mkdir -p ~/.codex/skills
ln -s /Users/rahuljain/work/eli5/skills/eli5 ~/.codex/skills/eli5
```

Per project:

```
mkdir -p <project>/.codex/skills
cp -r /Users/rahuljain/work/eli5/skills/eli5 <project>/.codex/skills/eli5
```

Codex loads skills automatically when a request matches the skill's description, so saying "eli5 this" in a prompt is enough. A symlink means updates to this repo apply immediately; a copy needs re-copying after changes.

## Repo layout

```
.claude-plugin/marketplace.json   Claude Code marketplace manifest
.claude-plugin/plugin.json        Claude Code plugin manifest
skills/eli5/SKILL.md              The skill itself (shared by Claude and Codex)
```

## Editing the skill

All behavior lives in `skills/eli5/SKILL.md`. Edit it, push, and reinstall or update in each tool.
