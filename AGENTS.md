# AGENTS.md

Guidance for AI coding agents working in this folder.

## What this project is

Reusable prompt library for learning from dense material and reviewing coding-agent output. This is a prompt/documentation folder, not an executable codebase.

## Layout

- `README.md` — main map of the coach families and usage patterns.
- `KNOWLEDGE_BASE.md` — living snapshot of the coach library. Load this first for substantive questions.
- `*.md` coach files — self-contained prompts.

## Knowledge Base

`KNOWLEDGE_BASE.md` is the concise handoff doc for this folder.

- **Read it first** when asked which coach to use, what families exist, or how the prompts fit together.
- **Update it** whenever:
  - a coach file is added, removed, or changes purpose
  - the recommended usage pipeline in `README.md` changes
  - provenance or source links change
- **Keep the prompt library honest.** Do not imply tooling or automation that does not exist.
- **Update `Last verified:`** whenever you materially edit the file.

## Conventions

- Coach files are self-contained prompts.
- Match each new coach to a specific situation; do not create overlapping prompts without saying why.
- Preserve the distinction between drilling coaches and review coaches.
- No extra files unless asked.

