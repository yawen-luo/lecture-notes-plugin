---
name: lecture-notes
description: Create and continuously refine one canonical, annotatable Notion Master Note per lecture from lecture slides/PDFs, transcripts, existing notes, and inline Notion comments. Use when the user asks to generate or organize lecture notes, check coverage, update the current Master Note, process comments attached to selected Notion text, or refine explanations in place.
---

# Lecture Notes — Notion Master Note Workflow

Use this skill for lecture-note work.

## Hard rule: one Notion chain

The persistent artifact for this workflow is **Notion only**.

Use ChatGPT's built-in Notion app to:
1. locate or create the lecture's canonical Master Note;
2. read it;
3. update it;
4. read its inline comments;
5. reply to comment discussions;
6. return the same page link.

Do not create or maintain a second canonical copy in another document system.
Do not hand the workflow to Work mode.
Do not use image generation as a substitute for a note.

The complete lecture-note workflow should run in the current ChatGPT conversation with the current course files plus the built-in Notion app.

## Core goal

Maintain **one increasingly good, editable, comment-friendly Notion Master Note per lecture**.

The note should support this loop:

```text
slides / transcript
      ↓
canonical Notion Master Note
      ↓
select text in Notion → add inline comment
      ↓
"处理评论"
      ↓
answer the discussion
+ improve the relevant body section
      ↓
continue studying and commenting on the improved note
```

Do not create a new Master Note for the same lecture when a clear existing one already exists.

## 1. Source scope

Default source scope:
- the slides/PDF/PPT/PPTX attached in the current chat;
- the transcript/recording text attached or pasted in the current chat;
- the explicitly named or located Notion Master Note.

Do not import unrelated course material from other chats, files, or web sources unless the user explicitly asks.

When the user asks to study, summarize, check, or answer from the lecture sources:
- ground the note in what those sources actually support;
- preserve their terminology, notation, organization, and level of detail;
- do not silently fill gaps with general knowledge;
- if extra explanation is added to answer the user's question, distinguish it from lecturer/source content when attribution matters.

## 2. Locate the canonical Notion Master Note

Before creating a page, determine whether this lecture already has one.

Use this order:

1. If the current conversation already contains the Notion page URL/ID created or used for this lecture, reuse it.
2. If the user explicitly provides a Notion page or says which page is the Master Note, use it.
3. Otherwise search Notion using the strongest identifiers available, such as:
   - course code;
   - lecture/topic number;
   - lecture title;
   - "Master Note".
4. Fetch the best matching candidate before editing it.
5. If one clear page matches the same lecture, reuse it.
6. If no matching page exists, create a standalone private Notion page.
7. If several plausible pages remain genuinely ambiguous, ask only when choosing the wrong one would materially risk editing the wrong lecture.

Once a page is chosen or created, it remains the canonical page for subsequent commands in the conversation.

## 3. Generate a lecture Master Note

When the user asks "生成课堂笔记", "整理这节课", "做成 Master Note", or equivalent:

1. Read the current slides and transcript before drafting.
2. Determine the **actual lecture coverage boundary** from the transcript:
   - what was taught;
   - where the lecturer stopped;
   - what the lecturer only previewed;
   - what exists on later slides but was not yet taught.
3. Internally scan for:
   - definitions / concepts;
   - formulas and symbol meanings;
   - proofs / derivations actually taught;
   - worked examples;
   - comparisons;
   - diagrams/circuits/architectures and their meaning;
   - lecturer additions, emphasis, warnings, and assumptions.
4. Draft a coherent lecture handout, not a slide-by-slide paraphrase.
5. Read `references/notion-style.md`.
6. Before the first Notion write in the conversation, read `notion://docs/enhanced-markdown-spec` through the Notion app.
7. Locate or create the canonical Notion page using Section 2.
8. Write or update the note in that page.
9. Fetch the page again after a substantial write and verify:
   - the intended content landed;
   - the hierarchy is correct;
   - untaught later-slide material was not mixed into taught content;
   - unrelated existing material was not damaged.
10. Return the Notion page link in the same chat.

### Coverage rules

- Do not omit a proof, derivation, formula, example, diagram, or lecturer addition merely because it seems detailed if it was taught.
- Do not merge distinct knowledge points just to shorten the note.
- Do not silently include slides beyond the transcript-defined stopping point as if they were taught.
- If later slides are worth retaining for orientation, place them in a clearly labeled "not yet taught / future coverage" section.
- Prefer a complete, readable note over a verbose coverage map.

## 4. Comment-friendly writing

The user annotates the page directly in Notion.

Therefore:
- write coherent but reasonably short blocks;
- keep one main idea per paragraph when practical;
- avoid giant paragraphs;
- use clear headings and local examples;
- do not hide core study content in toggles;
- do not create a database or dashboard by default.

The page should remain easy to select, comment on, and revise locally.

## 5. Process Notion comments — "处理评论"

This is a core workflow command.

When the user says "处理评论":

1. Identify the canonical Notion Master Note using Section 2.
2. Fetch the page with discussion context enabled.
3. Read comments/discussions across child blocks, including inline comments.
4. Focus on unresolved or newly updated study comments.
5. Avoid duplicating work: if a user question in a discussion has already been answered by the assistant and there is no newer user follow-up, skip it.
6. For each clear new question:
   - read the selected text and the nearby note context;
   - if needed, consult the current lecture slides/transcript so the explanation stays grounded;
   - answer the question accurately.
7. Decide whether the answer should improve the durable Master Note.

### 5.1 Durable conceptual answer → integrate into the body

For questions such as:
- "什么是 X？"
- "为什么？"
- "这个公式每个符号什么意思？"
- "这里怎么推出来的？"
- "举个例子"

when the explanation is useful for later review:

1. integrate it into the **smallest sensible nearby location** in the body;
2. make it read like normal lecture-note content, not pasted chat;
3. prefer a natural subsection, paragraph, example, definition, or intermediate derivation;
4. preserve the selected source text when possible so the comment anchor is not unnecessarily disturbed;
5. do **not** create a generic "AI 解释" block by default;
6. do **not** append the answer to a global Q&A section.

Then reply in the original Notion discussion with a concise answer and say that the useful explanation was integrated into the note.

### 5.2 Rewrite / correction comment → edit the target directly

For requests such as:
- "重写得更好懂"
- "这里有错"
- "这个符号不对"
- formatting / typo corrections

update the targeted passage directly, preserving the surrounding structure and course terminology, then reply in the original discussion.

### 5.3 Transient/meta comment → reply without bloating the note

If the comment is useful to answer but does not create durable study content, reply in the discussion without forcing it into the body.

### 5.4 Follow-up comments

If the user comments on material that was added during a previous comment-processing pass:
- treat it as a second-round study question;
- refine that same local section again;
- keep the note cohesive rather than building a visible Q&A chain.

### 5.5 Finish the pass

After processing one or more comments:
1. fetch the page again;
2. verify the edits landed in the intended sections;
3. preserve unrelated content;
4. do not claim comments are resolved unless the available Notion tool actually supports resolving them;
5. in chat, give a concise completion summary and the same Notion page link.

## 6. Other commands

Read `references/commands.md` for shorthand.

### "解释这里"

Explain the selected/current passage in chat only.
Do not edit the Notion note unless the user asks to write the explanation in.

### "重写这里"

Rewrite the targeted Notion passage in place for clarity.
Preserve knowledge content, technical terminology, notation, and lecture coverage.

### "检查完整性"

1. Locate/fetch the canonical Notion Master Note.
2. Compare it with the current lecture slides + transcript.
3. Identify omissions, incomplete explanations, and material that was included even though the lecturer had not reached it.
4. Repair the same Notion page in place.
5. Verify and return the same page link.
6. Do not dump a large audit table into chat unless the user explicitly asks to see the audit.

### "整理这节课"

Improve the same Notion page:
- hierarchy;
- readability;
- local ordering;
- accidental duplication;
- comment-friendliness.

Do not change the source-defined coverage boundary merely to make the note look more complete.

## 7. Notion editing discipline

Before editing an existing page:
- fetch it first;
- inspect the target and nearby section;
- make the smallest complete edit;
- preserve unrelated content.

Prefer targeted content updates over replacing the entire page when possible.

For substantial multi-part edits, fetch again afterward and verify.

Always return the canonical Notion page link after a create/update/comment-processing task.

## 8. Efficiency

Keep the workflow lightweight.

Do not create:
- a knowledge graph;
- a course database;
- confusion counters;
- slide-to-timestamp alignment;
- extra JSON state;
- duplicate note copies;

unless the user explicitly asks.

Spend effort on:
1. source-grounded coverage;
2. clear explanation;
3. correct local integration of answers;
4. reliable Notion editing;
5. preserving one canonical page.
