---
name: lecture-notes
description: Create and continuously refine complete course notes from lecture slides/PDFs, lecture transcripts or recordings, and existing notes. Use when the user asks to generate class notes, create or update a Notion Master Note, explain a passage from a Master Note, process comments attached to selected Notion text, merge a clarification back into the note, check coverage against course materials, reorganize a lecture note, or optionally export/update Google Docs.
---

# Lecture Notes Workflow

Use this skill for lecture-note work. Prefer the current chat's course materials and the user's explicitly named Master Note. Do not import unrelated course context from other chats or projects unless the user explicitly asks.

## Core goal

Maintain one increasingly good **editable Master Note per lecture**.

Default destination:
1. **Notion** — canonical Master Note.
2. **Google Docs** — optional fallback/export only when the user explicitly requests it or Notion is unavailable.

Core principles:
- Chat is the learning space.
- The Notion page is the durable artifact.
- Prefer **merge / replace** over appending repeated supplements.
- Use ChatGPT's existing multimodal and document understanding directly.
- Do not build a complex parsing/alignment pipeline unless the user explicitly asks.
- **Do not use image generation for lecture-note creation, formatting, diagrams, or document output unless the user explicitly asks for an image.** A note/page/document is not an image.

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
1. Generate the complete note.
2. Read `references/notion-style.md`.
3. Before the first Notion page write in the conversation, read `notion://docs/enhanced-markdown-spec` through the Notion app. Do not guess Notion markup.
4. If the user explicitly names an existing Notion page, update that page.
5. Otherwise create a new standalone private Notion page for the lecture. Do not automatically create a database or knowledge-management system.
6. Write the full note into the page.
7. Verify the created/updated page contains the intended note.
8. Return the Notion page reference/link.

If the user later provides a Lecture Notes database or parent page, use it as the destination for future notes after inspecting its schema/structure.

If Notion is unavailable:
- do not substitute image generation;
- produce the note in chat;
- if Google Drive is available, Google Docs may be used as a fallback only when appropriate or explicitly requested.

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
3. Read the current comments and the text/block they are attached to when available.
4. Prioritize unresolved/recent comments that clearly contain a question or instruction for GPT.
5. Answer those questions in chat first, grouped by their original location.
6. Do **not** automatically insert the full answer into the Master Note.
7. Do not claim to resolve a Notion comment unless the available Notion tool actually supports resolving discussions.

This preserves two layers:
- Notion page = clean long-term knowledge.
- comments/chat = temporary learning questions.

## 6. Interaction commands

Interpret these phrases as workflow commands even when the user does not use exact punctuation.

### “解释这里”
Explain the selected/current passage in chat only.
Do not change the Master Note.

### “写进笔记”
Take the useful understanding from the immediately preceding explanation/comment answer, compress it into note-quality prose, and merge it into the correct conceptual location in the Notion Master Note.
Do not paste the full chat explanation.
Prefer replacing or expanding the existing paragraph over adding a detached supplement.
Fetch the current page before editing, then update the smallest sensible section.

### “重写这里”
Rewrite the targeted passage for clarity while preserving its knowledge content and course terminology.
Replace the old explanation rather than appending a duplicate.

### “这个只是帮我理解，不要写进去”
Keep the explanation in chat only.

### “检查完整性”
Compare the current Master Note with the relevant slides + transcript.
Repair missing or incomplete knowledge points directly in the Notion Master Note when available.
Do not expose a large audit table unless useful or requested.

### “整理这节课”
Remove repetition caused by iterative edits, merge overlapping explanations, and normalize hierarchy/readability without losing unique knowledge.
Update the same Master Note rather than creating a second version.

### “处理评论”
Follow the Select-to-ask workflow above.

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

## 8. Editing principle

The Master Note should always represent the best current version, not the history of the conversation.

Bad:
- initial explanation
- supplement 1
- supplement 2
- follow-up answer
- another clarification at the bottom

Good:
- one integrated explanation in the concept's natural location.

**Merge, don't append.**

## 9. Efficiency

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
3. clean note structure;
4. high-quality incremental editing.
