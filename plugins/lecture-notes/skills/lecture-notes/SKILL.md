---
name: lecture-notes
description: Create and continuously refine complete course notes from lecture slides/PDFs, lecture transcripts or recordings, and existing notes. Use when the user asks to generate class notes, explain a passage from a Master Note, merge a clarification back into the note, check coverage against course materials, reorganize a lecture note, or process Google Docs comments on course notes.
---

# Lecture Notes Workflow

Use this skill for lecture-note work. Prefer the current chat's course materials and the user's explicitly named Master Note. Do not import unrelated course context from other chats or projects unless the user explicitly asks.

## Core goal

Maintain one increasingly good Master Note per lecture.

- Chat is the learning space.
- The Master Note is the durable artifact.
- Prefer **merge / replace** over appending repeated supplements.
- Use ChatGPT's existing multimodal and document understanding directly. Do not build or request a complex parsing/alignment pipeline unless the user explicitly asks.

## 1. Input handling

Expected inputs may include:
- PPT/PPTX/PDF lecture slides;
- lecture recording or transcript;
- existing notes;
- an existing Google Doc Master Note.

Process inputs quickly.

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

## 3. Writing style

The note should read like a clean lecture handout / textbook note, not an AI summary.

Default:
- Chinese explanation as the main language when the user is working in Chinese;
- keep important English technical terms;
- use natural paragraphs and clear headings;
- use bullet points only for true enumerations;
- avoid excessive bold text;
- avoid decorative emoji;
- let structure follow the subject instead of forcing every concept into the same template.

For mathematics / ECE:
- define symbols;
- keep derivations/proofs that were taught;
- make each transformation understandable.

For CS / AI:
- explain the problem, core idea, process/architecture, and contrasts when useful.

For circuits / logic:
- retain truth tables, expressions, mappings, and physical meaning where relevant.

## 4. Google Docs Master Note

When the user asks to create or update a Google Doc and a connected Google Drive/Docs tool is available:
1. Use the Google Doc as the canonical Master Note.
2. Read `references/google-doc-style.md` before formatting or reformatting it.
3. Preserve good existing content unless the user asked for content edits.
4. Do not change wording merely to make the document prettier.
5. After a substantive write, verify the intended content landed in the intended document.

If Google Docs tools are unavailable, produce the finished note in chat and state that the live Doc was not changed.

## 5. Interaction commands

Interpret these phrases as workflow commands even when the user does not use exact punctuation.

### “解释这里”
Explain the selected/current passage in chat only.
Do not change the Master Note.

### “写进笔记”
Take the useful understanding from the immediately preceding explanation, compress it into note-quality prose, and merge it into the correct conceptual location.
Do not paste the full chat explanation.
Prefer replacing or expanding the existing paragraph over adding a detached supplement.

### “重写这里”
Rewrite the targeted passage for clarity while preserving its knowledge content and course terminology.
Replace the old explanation rather than appending a duplicate.

### “这个只是帮我理解，不要写进去”
Keep the explanation in chat only.

### “检查完整性”
Compare the current Master Note with the relevant slides + transcript.
Repair missing or incomplete knowledge points.
Do not expose a large audit table unless useful or requested.

### “整理这节课”
Remove repetition caused by iterative edits, merge overlapping explanations, and normalize hierarchy/readability without losing unique knowledge.

### “处理评论”
If Google Docs comments are available:
1. Read unresolved comments and their quoted text.
2. Answer the questions first.
3. Do not automatically insert every long answer into the note.
4. When the user says “写进去”, patch the relevant original location.
5. Resolve comments only when the user's intent supports doing so.

## 6. Editing principle

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

## 7. Efficiency

This workflow is intentionally lightweight.

Do not create:
- a knowledge graph;
- a persistent database of every question;
- detailed slide-to-timestamp alignment;
- long-term confusion counters;
- extra JSON state;

unless the user explicitly asks for those features.

Spend model effort on:
1. complete coverage;
2. accurate explanation;
3. clean note structure;
4. high-quality incremental editing.
