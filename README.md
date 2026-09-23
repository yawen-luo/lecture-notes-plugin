# Lecture Notes Plugin

A lightweight, skills-only plugin for turning lecture slides and transcripts into a living Master Note.

## Core workflow

```text
PPT / PDF + transcript
        ↓
      ChatGPT
        ↓
 Google Docs Master Note
        ↕
question / comment / rewrite
        ↓
merge useful understanding back into the note
```

The plugin is intentionally simple: it relies on ChatGPT's existing document and multimodal understanding instead of building a separate parser, database, or knowledge graph.

## What it does

- Coverage-first lecture note generation.
- Preserves formulas, proofs, derivations, examples, and instructor additions when they were taught.
- Keeps chat explanations separate from the canonical Master Note unless the user asks to merge them.
- Supports commands such as `写进笔记`, `重写这里`, `检查完整性`, `整理这节课`, and `处理评论`.
- Uses Google Docs as the canonical note when a compatible connected Google Drive/Docs tool is available.
- Keeps formatting textbook-like: larger readable body text, few bullets, little bold, and only a few subtle highlight blocks.

## Structure

```text
.
├── .agents/plugins/marketplace.json
└── plugins/
    └── lecture-notes/
        ├── plugin.json
        └── skills/
            └── lecture-notes/
                ├── SKILL.md
                └── references/
                    ├── commands.md
                    └── google-doc-style.md
```

## Install for local testing

OpenAI supports repo-backed plugin marketplaces in ChatGPT desktop Work mode / Codex.

With Codex CLI:

```bash
codex plugin marketplace add yawen-luo/lecture-notes-plugin
```

Then open ChatGPT desktop, go to Plugins, select the marketplace **Yawen Lecture Tools**, and install **Lecture Notes**.

Availability can vary by product surface and rollout.

## Usage

Start a fresh chat, attach the lecture PPT/PDF and transcript, then say:

```text
生成课堂笔记
```

During study:

- `解释这里` — explain without editing the note.
- `写进笔记` — merge the useful explanation into the right place.
- `重写这里` — rewrite the targeted passage.
- `检查完整性` — compare against the source materials and repair omissions.
- `整理这节课` — remove redundancy and normalize structure.
- `处理评论` — process unresolved Google Docs comments when Docs access is available.

## Privacy

Do not commit copyrighted course slides, recordings, private notes, credentials, or API tokens to this repository.

## License

MIT
