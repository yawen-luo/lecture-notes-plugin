# Lecture Notes Plugin

A lightweight ChatGPT/Codex plugin for turning lecture slides and transcripts into a living Master Note.

**v0.2.1 is Notion-first and Chat-first.** Notion is the canonical editable note. The complete workflow should run directly in the current ChatGPT conversation. Google Docs is an optional fallback/export destination.

## Execution rule

Lecture-note work should **not be automatically handed off to Work mode**.

The following are expected to run directly in the current chat:
- reading PPT/PDF + transcript;
- generating the note;
- creating/updating the Notion Master Note;
- checking coverage;
- reading Notion comments;
- inserting answers beside selected text;
- second-round follow-up;
- ordinary restructuring and edits.

Task length, transcript size, or multiple tool calls are not reasons to switch modes.

Work is only appropriate when the user explicitly asks to use Work.

## Core workflow

```text
PPT / PDF + transcript
        ↓
 current ChatGPT chat
        ↓
  Notion Master Note
        ↕
select text → inline comment
        ↓
   “处理评论”
        ↓
answer inserted beside the selected material
        ↓
select part of the answer → ask again
```

## What v0.2.1 implements

- Notion-first canonical Master Note.
- Chat-first execution: no automatic Work handoff.
- Coverage-first lecture note generation.
- Preserves formulas, proofs, derivations, examples, and instructor additions when taught.
- Creates a standalone private Notion page by default when no destination is specified.
- Supports select-to-ask using Notion inline comments.
- Inserts answers directly next to the questioned content for iterative follow-up.
- Keeps those explanations in the note unless the user explicitly asks to merge/rewrite/remove them.
- Keeps Google Docs available as optional export/fallback.
- Explicitly forbids image generation as a substitute for notes/documents.

## What it deliberately does NOT do

- No automatic Work delegation.
- No automatic course database.
- No knowledge graph.
- No long-term confusion tracking.
- No detailed slide/audio alignment.
- No duplicate canonical copy in both Notion and Google Docs.

## Install / refresh for local testing

```bash
codex plugin marketplace upgrade
```

Then fully quit and reopen ChatGPT desktop. If the installed plugin still shows an older version, uninstall and reinstall **Lecture Notes** from **Yawen Lecture Tools**.

## Usage

Attach the lecture PPT/PDF and transcript, then say:

```text
生成课堂笔记
```

The plugin should complete the task directly in the current chat and create/update the Notion Master Note.

During study:
- Select text in Notion and add a comment such as `GPT：这里为什么？`
- Return to ChatGPT and say `处理评论`
- The answer is inserted directly beside the selected text.
- You can select part of that answer and ask a second-round question.

## Privacy

Do not commit copyrighted course slides, recordings, private notes, credentials, or API tokens to this repository.

## License

MIT
