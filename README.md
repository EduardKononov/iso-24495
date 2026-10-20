# ISO 24495 Plain Language Skills

Five [Agent Skills](https://code.claude.com/docs/en/skills) that support plain language writing and code. They apply principles inspired by the ISO 24495 *Plain language* series.

The skills are plain `SKILL.md` files with agent-neutral wording. Any tool that reads the Agent Skills format can use them.

This repository also packages them as a Claude Code plugin with an **ISO 24495 output style** (`claude/output-styles/iso-24495.md`). Select the style with `/output-style` to hold every response to the core rules without relying on skill activation.

## Skills

| Skill | Scope |
|-------|-------|
| `iso-24495-1` | **Core principles.** Governs all user-facing output: no filler preambles, short sentences and paragraphs, active voice, scannable structure, concrete instructions. |
| `iso-24495-2` | **Legal writing.** Extends the core skill for contracts, licences, and compliance text: standardised modal verbs, no legalese, named actors, structured conditional clauses, defined terms, cross-references that name what they point at, stable clause identifiers, a summary layer over the operative text, and section names a reader can navigate by. |
| `iso-24495-3` | **Science and technical writing.** Extends the core skill for documentation, architecture, and code review: progressive disclosure, exact file citations, defined acronyms, text alternatives for diagrams, and the stages placed inside the document levels of `iso-24495-5`. |
| `iso-24495-5` | **Document design (provisional).** Extends the core skill for structuring complex documents: an opening block, visual hierarchy, navigation aids, layered detail, comparisons, consistent signalling, and a signpost for the reader who wanted a different document. Ships a decision record, a runbook and a design document template. Based on the unpublished ISO/WD 24495-5 working draft. |
| `iso-24495-code` | **Plain language in code.** Applies the principles to what a person reads in source: the order units appear in, their names, what comments say, and what an error tells the reader who hits it. Measured to change how Claude structures a file, at no cost to correctness. |

The core skill activates the relevant writing skills automatically. It triggers `iso-24495-2` for legal content, `iso-24495-3` for technical content, and `iso-24495-5` for complex documents. A legal document always pairs with `iso-24495-5`, and a technical one does whenever its output is a document.

All skills exempt internal reasoning. The writing skills preserve code blocks, commands, and logs untouched; `iso-24495-code` is the exception, because governing code is its subject. Technical and legal accuracy always supersede formatting rules.

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

Every skill carries `agents/openai.yaml`, which gives Codex its display name, its short description, and the prompt Codex offers for it. Invoke a skill by name, as in `$iso-24495-1`, or ask for it in words.

Codex has no output style, so the same rules are a skill there: `iso-24495-style` holds the output style word for word, and a test keeps the two identical. It lives in `codex-skills/` rather than `skills/`, because Claude Code scans `skills/` and would otherwise offer a skill its output style already covers. Codex reads both directories, named in `.codex-plugin/plugin.json`.

Name the skill in your `AGENTS.md` to apply it to every response:

```
Apply `iso-24495-style` to every response.
```

Put that in your project's `AGENTS.md` or in `~/.codex/AGENTS.md`. An `AGENTS.md` inside a plugin is ignored, so a plugin cannot apply itself. For a single reply, invoke `$iso-24495-style` instead.

## Installation (Cursor)

Cursor loads this repository as a plugin from `.cursor-plugin/plugin.json`. The manifest points at the five shared skills in `skills/`. Cursor has no output style, so `cursor/rules/iso-24495.mdc` is an always-on rule. Once the plugin is installed, it applies the output style to every response. A test keeps that rule identical to `claude/output-styles/iso-24495.md`.

To try the plugin locally, copy this repository into `~/.cursor/plugins/local/iso-24495-plain-language`, then reload Cursor. A symlink to this repository is skipped, because Cursor only follows a symlink whose target stays inside that local folder.

Publishing is at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish).

## Usage

Once installed, the agent loads the skills when their descriptions match the task. To apply one explicitly, ask for it by name, for example: "Apply `iso-24495-2` to this licence text."

To enforce the core skill on every response, add a line to your agent's instruction file (`CLAUDE.md`, `AGENTS.md`, or equivalent):

```markdown
- ALWAYS activate and adhere to the `iso-24495-1` Plain Language skill across all responses
```

For agents without a plugin system, copy the `skills/` subdirectories into wherever the tool discovers skills.

## Disclaimer

This unofficial project is not affiliated with, endorsed by, or approved by the International Organization for Standardization (ISO). The skills contain original guidance inspired by the ISO 24495 series. They do not reproduce the text of any ISO standard.

Publication status: Part 1 published 2023, Part 2 August 2025, Part 3 May 2026. Part 5 remains an unpublished draft (ISO/WD 24495-5). Its skill is provisional guidance from the public scope statement, to be revised when ISO publishes.

**Conformance disclaimer.** The full ISO 24495 texts are licensed and have not been consulted. These skills are built from public principles, published scopes, and common plain-language practice.

The principles derive from the International Plain Language Federation's freely published framework. Every quantitative rule here (sentence length, paragraph density, legalese, heading depth) is this project's own proxy. No rule is a clause of any standard.

Nothing this plugin produces is a statement of ISO conformance. No certification scheme exists for ISO 24495. "Aligned" in the skills means aligned with this project's interpretation, nothing more.

## Reference

Read the standard rather than this project's reading of it.

- **[ISO 24495-1:2023, Plain language, Part 1: Governing principles and guidelines](https://www.iso.org/standard/78907.html)**, the published standard these skills interpret. The ISO catalogue also carries Part 2 (legal writing) and Part 3 (science and technical communication).
- **[The International Plain Language Federation's definition and framework](https://www.iplfederation.org/iso-standard/)**, freely published, and the source of the four governing principles used here.
- **[Plain Language Association International on the ISO standard](https://plainlanguage.com/what-is-plain-language/iso-plain-language-standard/)**, background on how the standard was drafted and what it covers.

The ISO texts are licensed, so the standards themselves cost money. Everything in this repository is built from the freely published material above.

## TypeScript style

This project follows the [Google TypeScript Style Guide](https://google.github.io/styleguide/tsguide.html). It uses kebab-case filenames instead of snake_case and double quotes instead of single quotes. Both deviations match the wider ecosystem.

## Roadmap

What remains:

- **When ISO publishes Part 5:** revise the provisional `iso-24495-5` skill against the published text.

Plain-language checks on script comments were once planned for this release. That plan is cancelled. Comments are fragments, and checking them well would cost more machinery than the advice is worth.

## Licence

MIT
