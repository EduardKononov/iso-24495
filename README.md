# Plain language skills

Two [Agent Skills](https://code.claude.com/docs/en/skills) that support plain language writing.

The skills are plain `SKILL.md` files with agent-neutral wording. Any tool that reads the Agent Skills format can use them.

This repository also packages them as a Claude Code plugin with a **Response style** output style (`claude/output-styles/response-style.md`). Select the style with `/output-style` to hold every response to the core rules without relying on skill activation.

## Skills

| Skill | Scope |
|-------|-------|
| `plain-language` | **Plain language.** Governs all user-facing output: no filler preambles, short sentences and paragraphs, active voice, scannable structure, concrete instructions. |
| `technical-explanation` | **Technical explanation.** Tells the agent how to explain code and technical ideas to a software developer: what it is for, how the parts relate, then the code, with the file and the lines cited in the host's form. |

`plain-language` triggers `technical-explanation` when a reply explains how something works or why it is built that way.

All skills exempt internal reasoning. The writing skills preserve code blocks, commands, and logs untouched. Technical accuracy and factual correctness always supersede formatting rules.

## Installation (Claude Code)

Add this repository as a plugin marketplace, then install the plugin:

```
/plugin marketplace add https://github.com/GaZmagik/iso-24495.git
/plugin install iso-24495-plain-language@iso-24495
```

Use the full HTTPS address as shown. The short `owner/repo` form makes some Claude Code versions clone over SSH, which fails without GitHub SSH keys.

Or from a local clone:

```
/plugin marketplace add ./path/to/this/repo
/plugin install iso-24495-plain-language@iso-24495
```

## Installation (Codex CLI)

Codex reads the same marketplace manifest, so the plugin installs from the same address:

```
codex plugin marketplace add https://github.com/GaZmagik/iso-24495.git
codex plugin add iso-24495-plain-language@iso-24495
```

Or from a local clone, where `.` is the repository root:

```
codex plugin marketplace add .
codex plugin add iso-24495-plain-language@iso-24495
```

Every skill carries `agents/openai.yaml`, which gives Codex its display name, its short description, and the prompt Codex offers for it. Invoke a skill by name, as in `$plain-language`, or ask for it in words.

Codex has no output style, so the same rules are a skill there: `response-style` holds the output style word for word. It lives in `codex-skills/` rather than `skills/`, because Claude Code scans `skills/` and would otherwise offer a skill its output style already covers. Codex reads both directories, named in `.codex-plugin/plugin.json`.

Name the skill in your `AGENTS.md` to apply it to every response:

```
Apply `response-style` to every response.
```

Put that in your project's `AGENTS.md` or in `~/.codex/AGENTS.md`. An `AGENTS.md` inside a plugin is ignored, so a plugin cannot apply itself. For a single reply, invoke `$response-style` instead.

## Installation (Cursor)

Cursor loads this repository as a plugin from `.cursor-plugin/plugin.json`. The manifest points at the two shared skills in `skills/`. Cursor has no output style, so `cursor/rules/response-style.mdc` is an always-on rule. Once the plugin is installed, it applies the output style to every response.

To try the plugin locally, copy this repository into `~/.cursor/plugins/local/iso-24495-plain-language`, then reload Cursor. A symlink to this repository is skipped, because Cursor only follows a symlink whose target stays inside that local folder.

Publishing is at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish).

## Usage

Once installed, the agent loads the skills when their descriptions match the task. To apply one explicitly, ask for it by name, for example: "Apply `technical-explanation` to how this rate limiter works."

To enforce the core skill on every response, add a line to your agent's instruction file (`CLAUDE.md`, `AGENTS.md`, or equivalent):

```markdown
- ALWAYS activate and adhere to the `plain-language` skill across all responses
```

For agents without a plugin system, copy the `skills/` subdirectories into wherever the tool discovers skills.

## Disclaimer

This unofficial project is not affiliated with, endorsed by, or approved by the International Organization for Standardization (ISO). The skills contain original guidance inspired by the ISO 24495 series. They do not reproduce the text of any ISO standard.

**Conformance disclaimer.** The full ISO 24495 texts are licensed and have not been consulted. These skills are built from public principles, published scopes, and common plain-language practice.

The principles derive from the International Plain Language Federation's freely published framework. The quantitative rules are this project's own proxies. No rule is a clause of any standard.

Nothing this plugin produces is a statement of ISO conformance. No certification scheme exists for ISO 24495.

## Reference

Read the standard rather than this project's reading of it.

- **[ISO 24495-1:2023, Plain language, Part 1: Governing principles and guidelines](https://www.iso.org/standard/78907.html)**, the published standard these skills interpret.
- **[The International Plain Language Federation's definition and framework](https://www.iplfederation.org/iso-standard/)**, freely published, and the source of the four governing principles used here.

The ISO texts are licensed, so the standards themselves cost money. Everything in this repository is built from the freely published material above.

## Licence

MIT
