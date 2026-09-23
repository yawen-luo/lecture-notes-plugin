# Lecture Notes Plugin

A lightweight ChatGPT/Codex plugin for turning lecture slides, transcripts, and study comments into one living **Notion Master Note per lecture**.

## v0.3.0: Notion-only

The plugin now has one persistent workflow only:

```text
PPT / PDF + transcript
        ↓
current ChatGPT conversation
        ↓
canonical Notion Master Note
        ↓
select text → inline comment
        ↓
“处理评论”
        ↓
answer the comment discussion
+ improve the relevant body section
        ↓
continue annotating the same page
```

The built-in Notion app is required. The plugin does not maintain a parallel document copy.

## Core behavior

### Generate notes

When asked to generate/organize a lecture note, the plugin:

1. reads the current lecture slides and transcript;
2. determines what the lecturer actually covered;
3. locates an existing Notion Master Note for the same lecture or creates one if none exists;
4. writes a clean, comment-friendly note;
5. verifies the page;
6. returns the Notion link.

It reuses the same page for later updates instead of creating duplicates.

### Check coverage

When asked to check completeness, the plugin compares the existing Notion note with the slides/transcript and repairs the same page in place.

It should catch both:
- missing taught knowledge;
- later-slide material that was written as if it had already been taught.

### Process comments

The intended study interaction is:

1. select text in Notion;
2. add an inline comment such as `什么是 transistor？`;
3. return to ChatGPT and say `处理评论`.

The plugin then:

1. reads the unresolved/new comment and selected context;
2. answers the question;
3. integrates durable conceptual explanations into the smallest sensible nearby place in the note;
4. replies in the original Notion comment discussion;
5. verifies the edit;
6. returns the same Notion page link.

The default is **not** to accumulate "AI explanation" blocks or a Q&A appendix. Useful answers should improve the Master Note itself.

For typo, rewrite, notation, or formatting comments, the plugin edits the target directly and replies to the thread.

## Comment-friendly note design

Master Notes use:
- clear H1/H2/H3 hierarchy;
- coherent, reasonably short paragraphs;
- one main idea per block when practical;
- preserved formulas, derivations, examples, mappings, and circuit meaning;
- a small number of meaningful callouts.

Core content should not be hidden inside complex layouts or toggles because the page is meant to be selected and annotated.

## Source discipline

The current lecture slides/transcript define the note's factual and coverage basis.

- Preserve terminology and notation from the course.
- Keep lecturer additions that were actually taught.
- Do not silently add later-slide material as if it was covered.
- Do not silently fill source gaps with general knowledge.
- Extra explanations added for study questions should not be falsely attributed to the lecturer.

## Execution

The workflow runs directly in the current ChatGPT conversation with the course files and the built-in Notion app.

Do not automatically delegate lecture-note work to Work mode.
Do not use image generation as a substitute for the note.

## Install / refresh for local testing

```bash
codex plugin marketplace upgrade
```

Then fully quit and reopen ChatGPT desktop. If the installed plugin still shows an older version, uninstall and reinstall **Lecture Notes** from **Yawen Lecture Tools**.

## Usage

Attach the lecture PPT/PDF and transcript, then invoke Lecture Notes and say:

```text
生成课堂笔记
```

During study:

```text
处理评论
```

For source comparison:

```text
检查完整性
```

## Privacy

Do not commit copyrighted course slides, recordings, private notes, credentials, or API tokens to this repository.

## License

MIT
