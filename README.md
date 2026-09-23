# Lecture Notes Plugin

A lightweight ChatGPT/Codex plugin for turning lecture slides and transcripts into a living Master Note.

**v0.2.0 is Notion-first.** Notion is the canonical editable note; Google Docs is an optional fallback/export destination.

## Core workflow

```text
PPT / PDF + transcript
        ↓
      ChatGPT
        ↓
  Notion Master Note
        ↕
select text → inline comment
        ↓
   “处理评论”
        ↓
 explanation in chat
        ↓
   “写进笔记”
        ↓
merge back into the original section
```

The plugin intentionally relies on ChatGPT's existing document/multimodal understanding instead of building a separate parser, database, or knowledge graph.

## What v0.2.0 implements

- Coverage-first lecture note generation.
- Preserves formulas, proofs, derivations, examples, and instructor additions when taught.
- Creates a standalone private Notion page by default when no destination is specified.
- Supports a select-to-ask workflow using Notion inline comments.
- Keeps temporary explanations in chat until the user explicitly says `写进笔记`.
- Merges useful explanations back into the correct original section instead of appending supplements.
- Supports `重写这里`, `检查完整性`, `整理这节课`, and `处理评论`.
- Uses restrained Notion formatting: natural paragraphs, clear headings, few bullets, little bold, and a small number of meaningful callouts.
- Keeps Google Docs available as an optional export/fallback.
- Explicitly forbids image generation as a substitute for notes/documents.

## What v0.2.0 deliberately does NOT do

- It does not automatically create a course database.
- It does not build a knowledge graph.
- It does not keep a long-term confusion counter.
- It does not perform detailed slide-to-audio timestamp alignment.
- It does not maintain duplicate canonical copies in both Notion and Google Docs.

If you later provide a Lecture Notes database or parent page, the plugin can use that as the destination for future notes.

## Structure

```text
.
├── .agents/plugins/marketplace.json
└── plugins/
    └── lecture-notes/
        ├── plugin.json
        ├── .app.json
        └── skills/
            └── lecture-notes/
                ├── SKILL.md
                ├── agents/openai.yaml
                └── references/
                    ├── commands.md
                    ├── notion-style.md
                    └── google-doc-style.md
```

## Install / refresh for local testing

```bash
codex plugin marketplace add yawen-luo/lecture-notes-plugin
codex plugin marketplace upgrade
```

Then restart ChatGPT desktop, open Plugins, select **Yawen Lecture Tools**, and install/refresh **Lecture Notes**.

## Usage

Attach the lecture PPT/PDF and transcript, then say:

```text
生成课堂笔记
```

During study:

- Select text in Notion and add a comment such as `GPT：这里为什么？`
- Return to ChatGPT and say `处理评论`
- After the explanation, say `写进笔记` only if you want the useful part merged into the permanent note.

## Privacy

Do not commit copyrighted course slides, recordings, private notes, credentials, or API tokens to this repository.

## License

MIT
