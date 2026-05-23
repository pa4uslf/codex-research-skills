# Codex Setup

This fork exposes the Academic Research Skills repository as a Codex plugin.
The upstream Claude Code skill folders stay at the repository root; Codex loads
small wrapper skills from `plugin/codex-skills/` and those wrappers point back
to the canonical workflow files.

## Install From This Fork

```bash
codex plugin marketplace add pa4uslf/codex-research-skills --ref main
codex plugin add codex-research-skills@codex-research-skills
```

For local development from a checkout:

```bash
cd /path/to/codex-research-skills
codex plugin marketplace add .
codex plugin add codex-research-skills@codex-research-skills
```

Restart Codex after installing so the plugin skills are included in the next
session context.

## Available Codex Skills

Use the `$skill-name` form in Codex:

| Codex skill | Use when |
|---|---|
| `$academic-research-suite` | You want Codex to choose between research, writing, review, or the full pipeline. |
| `$ars-deep-research` | You need literature review, systematic review, PRISMA, evidence synthesis, fact-checking, or guided research scoping. |
| `$ars-academic-paper` | You need to write, outline, revise, format, cite-check, or generate disclosure text for an academic paper. |
| `$ars-paper-reviewer` | You need a structured manuscript review, peer-review simulation, methodology focus, re-review, or reviewer calibration. |
| `$ars-academic-pipeline` | You want the end-to-end research-to-publication workflow with integrity checks and review stages. |

The original Claude slash commands under `commands/` are retained as reference
prompts. In Codex, prefer the `$skill-name` entrypoints above.

## Validate The Package

From the repository root:

```bash
python3 scripts/check_data_access_level.py
python3 scripts/check_task_type.py
python3 scripts/check_version_consistency.py
codex plugin marketplace add .
codex plugin list
codex plugin add codex-research-skills@codex-research-skills
```

The `codex plugin marketplace add .` and `codex plugin add ...` commands write
to the active Codex config. For CI or dry-run style validation, run them with an
isolated `HOME` pointing at a temporary directory.

## Packaging Notes

- `plugin/.codex-plugin/plugin.json` is the Codex plugin manifest.
- `.codex-plugin/marketplace.json` and `.agents/plugins/marketplace.json` let
  `codex plugin marketplace add .` discover the local plugin across current
  Codex marketplace loaders.
- `plugin/codex-skills/*/SKILL.md` files are Codex wrappers. They intentionally do not
  duplicate the full upstream workflow bodies.
- `skills/` remains the Claude plugin symlink layout and is not used by the
  Codex plugin manifest.
- Root skill folders such as `deep-research/` and `academic-paper/` remain the
  canonical content shared with Claude Code users.
