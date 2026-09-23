---
name: lecture-notes
description: Create and continuously refine complete course notes from lecture slides/PDFs, lecture transcripts or recordings, and existing notes. Use when the user asks to generate class notes, create or update a Notion Master Note, process comments attached to selected Notion text, insert explanations beside the questioned material for iterative follow-up, check coverage against course materials, reorganize a lecture note, or optionally export/update Google Docs.
---

# Lecture Notes Workflow

Use this skill for lecture-note work. Prefer the current chat's course materials and the user's explicitly named Master Note. Do not import unrelated course context from other chats or projects unless the user explicitly asks.

## Core goal

Maintain one increasingly good **editable Master Note per lecture**.

Default destination:
1. **Notion** — canonical Master Note.
2. **Google Docs** — optional fallback/export only when the user explicitly requests it or Notion is unavailable.

Core principles:
- The Notion page is the primary study surface and durable artifact.
- Explanations inserted while studying are part of the note unless the user later asks to rewrite or remove them.
- Prefer local insertion near the questioned material over collecting answers at the end.
- Use ChatGPT's existing multimodal and document understanding directly.
- Do not build a complex parsing/alignment pipeline unless the user explicitly asks.
- **Do not use image generation for lecture-note creation, formatting, diagrams, or document output unless the user explicitly asks for an image.** A note/page/document is not an image.

## Execution mode constraint — hard rule

This workflow is designed to be completed **inside the current ChatGPT conversation** with the available file-reading and connected-app tools.

- **Do not automatically create, delegate, or hand off this task to Work mode.**
- Do not say that the task has been “given to Work”, “handed to Work”, or that Work will finish it.
- The size of the PPT, length of the transcript, number of steps, need to create a Notion page, need to process comments, or need to make multiple tool calls are **not** reasons to switch to Work.
- Complete lecture-note generation, Notion creation/editing, coverage checks, comment processing, and iterative follow-up directly in the current chat.
- Use Work **only when the user explicitly asks in the current request to use Work / Work mode**.
- If the current chat genuinely lacks a required tool or permission, state that specific limitation and complete everything else possible in the current chat. Do not autonomously switch modes as a workaround.
- Do not consume Work/Codex quota for this workflow merely because the task is long or multi-step.

## 1. Input handling

Expected inputs may include:
- PPT/PPTX/PDF lecture slides;
- lecture recording or transcript;
- existing notes;
- an existing Notion Master Note;
- an optional Google Doc.

For slides + transcript:
1. Scan both sources before drafting.
2. Determine the actual scope taught in class.
3. Use the transcript mainly to:
   - determine where the lecturer actually stopped;
   - recover lecturer explanations, examples, comparisons, emphasis, and additions not written on slides;
   - interpret sparse slides.
4. Do **not** perform minute-by-minute alignment or generate a large coverage table unless the user asks.
5. When transcript wording is noisy, use slide terminology and context to repair obvious transcription errors. Do not invent material and attribute it to the lecturer.

## 2. Coverage-first note generation

Before writing, perform a lightweight internal coverage scan. Do not print it unless requested.

Check for:
- concepts and definitions;
- formulas and symbol meanings;
- proofs and derivations actually taught;
- worked examples;
- comparisons;
- diagrams/circuit/architecture meaning when relevant;
- lecturer additions and emphasis;
- content the lecturer skimmed or skipped.

Then draft the note.

Before finishing, compare the draft against the slides and transcript again and repair important omissions.

### Non-negotiable coverage rules

- Do not merely paraphrase slides page by page.
- Do not omit a proof, derivation, formula, example, or diagram because it seems "too detailed" if the class covered it.
- Do not merge distinct knowledge points just to make the structure shorter.
- Preserve course terminology, notation, formulas, and meaningful ordering.
- Distinguish lecturer content from later explanatory additions when attribution matters.

## 3. Default output: Notion Master Note

When the Notion app is available, creating or updating the editable Notion Master Note is part of task completion for requests such as:
- “生成课堂笔记”
- “整理这节课”
- “做成 Master Note”

Workflow:
1. Generate the complete note in the current chat session.
2. Read `references/notion-style.md`.
3. Before the first Notion page write in the conversation, read `notion://docs/enhanced-markdown-spec` through the Notion app. Do not guess Notion markup.
4. If the user explicitly names an existing Notion page, update that page.
5. Otherwise create a new standalone private Notion page for the lecture. Do not automatically create a database or knowledge-management system.
6. Write the full note into the page.
7. Verify the created/updated page contains the intended note.
8. Return the Notion page reference/link in the same conversation.

If the user later provides a Lecture Notes database or parent page, use it as the destination for future notes after inspecting its schema/structure.

If Notion is unavailable:
- do not substitute image generation;
- produce the note in chat;
- if Google Drive is available, Google Docs may be used as a fallback only when appropriate or explicitly requested;
- do not hand the task to Work.

## 4. Writing style

The note should read like a clean lecture handout / textbook note, not an AI summary.

Default:
- Chinese explanation as the main language when the user is working in Chinese;
- keep important English technical terms;
- use natural paragraphs and clear headings;
- use bullet points only for true enumerations;
- avoid excessive bold text;
- avoid decorative emoji;
- use a small number of meaningful Notion callout/highlight blocks;
- let structure follow the subject instead of forcing every concept into the same template.

For mathematics / ECE:
- define symbols;
- keep derivations/proofs that were taught;
- make each transformation understandable.

For CS / AI:
- explain the problem, core idea, process/architecture, and contrasts when useful.

For circuits / logic:
- retain truth tables, expressions, mappings, and physical meaning where relevant.

## 5. Select-to-ask workflow in Notion

The intended study interaction is:

**Select text in Notion → add an inline comment → return to ChatGPT → say “处理评论”.**

The user's comment may be short, for example:
- “GPT：这里为什么？”
- “GPT：举个例子”
- “GPT：这个公式每个符号什么意思？”
- “GPT：重写得更好懂”

When the user says “处理评论”:
1. Identify the relevant Notion Master Note from the conversation.
2. Fetch the page with discussion/comment context.
3. Read unresolved/recent comments and the text/block they are attached to when available.
4. Generate a useful explanation for each clear question.
5. **Insert the explanation directly into the Notion page immediately after the questioned paragraph/block, or at the smallest sensible nearby location.**
6. Use a consistent visually distinct label such as **“AI 解释”** or **“学习解释”**.
7. Keep the answer detailed enough to support understanding.
8. If several comments refer to different locations, place each answer at its own original location rather than collecting answers at the end.
9. Verify the insertions landed near the intended source material.
10. In chat, give only a concise completion summary and the page link unless the user asks to also see the answer in chat.

### Second-round follow-up

Inserted explanation blocks are intentionally selectable.

If the user selects text inside an inserted explanation block, adds another comment, and says “处理评论” again:
- treat it as a chained follow-up;
- insert the next explanation immediately after the explanation block being questioned;
- preserve the local question → answer → follow-up sequence;
- do not move the thread to the end of the page.

These inserted explanations remain part of the note. Do **not** automatically remove, merge, or rewrite them later.

Only rewrite, merge, or delete them when the user explicitly asks, for example:
- “把这段问答整理成正式笔记”
- “去掉问答痕迹”
- “重写这一节”
- “删除这些 AI 解释”

Do not claim to resolve a Notion comment unless the available Notion tool actually supports resolving discussions.

## 6. Interaction commands

Interpret these phrases as workflow commands even when the user does not use exact punctuation.

### “解释这里”
Explain the selected/current passage in chat only.
Do not change the Master Note.

### “处理评论”
Read the Notion comments and insert answers directly beside the questioned material so the user can continue selecting and asking follow-up questions.

### “重写这里”
Rewrite the targeted passage for clarity while preserving its knowledge content and course terminology.
Replace the old explanation rather than appending a duplicate.

### “检查完整性”
Compare the current Master Note with the relevant slides + transcript.
Repair missing or incomplete knowledge points directly in the Notion Master Note when available.
Do not expose a large audit table unless useful or requested.

### “整理这节课”
Improve structure, remove accidental duplication, and normalize hierarchy/readability without automatically deleting or merging the user's inserted AI explanation blocks.
Only transform those explanation blocks when the user explicitly asks.

### “导出到 Google Docs”
Create/update a Google Docs copy when explicitly requested.

## 7. Google Docs optional fallback/export

Use Google Docs only when:
- the user explicitly requests Google Docs;
- the user wants print/PDF/formal-document-oriented formatting;
- Notion is unavailable and Google Drive is an appropriate fallback.

When using Google Docs:
1. Read `references/google-doc-style.md`.
2. Preserve good existing content.
3. Do not change wording merely to make the document prettier.
4. Verify the write landed in the intended document.

Do not maintain two canonical copies by default. Notion remains canonical unless the user explicitly changes the preference.

## 8. Efficiency

This workflow is intentionally lightweight.

Do not create:
- a knowledge graph;
- a persistent database of every question;
- detailed slide-to-timestamp alignment;
- long-term confusion counters;
- extra JSON state;
- an automatic course database unless the user asks;

unless the user explicitly asks for those features.

Spend model effort on:
1. complete coverage;
2. accurate explanation;
3. local, easy-to-follow iterative Q&A in the note;
4. high-quality incremental editing.
