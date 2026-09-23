# Notion Master Note Style

Load this reference whenever creating, updating, auditing, or processing comments on the canonical Notion Master Note.

## Principle

The page should feel like a clean lecture handout / textbook note that is easy to annotate directly in Notion.

The user studies by selecting text and attaching inline comments, so write in **comment-friendly blocks**:
- one coherent idea per paragraph/block when practical;
- avoid giant paragraphs that contain many unrelated ideas;
- keep headings and examples close to the concept they explain;
- do not hide core material inside toggles;
- do not create databases, dashboards, columns, or complex layouts unless explicitly requested.

## Default structure

- Use the page title for the lecture title; do not repeat it as the first body heading.
- Use H1/H2/H3 based on the actual knowledge structure.
- Use normal paragraphs as the default.
- Use bullet lists only for true enumerations.
- Use bold sparingly.
- Avoid decorative emoji in the body.
- Use only a small number of meaningful callouts.
- Preserve course terminology, notation, formulas, tables, mappings, circuits, and worked examples when they are part of the taught content.

## Coverage boundary

The transcript determines what was actually taught.

- Slides beyond the lecturer's stopping point must not be silently written as if they were taught.
- If later slides are useful to mention, mark them clearly as not yet taught / future coverage rather than mixing them into the current lecture.
- Lecturer additions that are not written on the slides should be preserved when they materially help understanding.
- Do not fill source gaps with outside knowledge unless the user explicitly asks for expansion. If extra explanation is added to answer a study question, make it a clear explanatory addition rather than falsely attributing it to the lecturer.

## Comment-processing edits

The default goal is **not** to accumulate visible Q&A or "AI explanation" blocks. The goal is to make the Master Note itself better.

When a comment asks a durable conceptual question:
- answer the question;
- integrate the useful explanation into the smallest sensible nearby location in the body;
- use a natural subsection, paragraph, example, definition, derivation, or clarification that reads as part of the note;
- keep the original selected text intact when possible so the comment anchor is not needlessly disturbed;
- reply in the original Notion discussion with a concise answer and note that the explanation was integrated.

Examples of durable material that normally belongs in the body:
- "what is X?" definitions;
- why a formula or transformation works;
- symbol meanings;
- a missing intermediate derivation;
- a concrete example needed to understand a concept;
- a clarification that prevents a recurring misconception.

Comments that are mainly editorial or transient should usually be handled directly instead of creating new study content:
- typo / notation correction → correct the text and reply;
- "rewrite this more clearly" → replace the passage and reply;
- formatting request → fix formatting and reply;
- a meta question that does not improve the note → answer in the comment thread without forcing it into the body.

If the user comments on a newly added explanation, treat it as a second-round study question and refine that same local section again.

Do not automatically append a Q&A section at the end of the page.
Do not label every inserted explanation as "AI 解释".
Do not claim a comment is resolved unless the available Notion tool actually resolves discussions.

## Formulas and technical material

- Preserve equations and mathematical notation.
- Use the current Notion enhanced Markdown specification instead of guessing syntax.
- Keep derivations understandable step by step when they were taught or are needed to answer the user's question.
- For ECE / logic, retain truth tables, expressions, mappings, circuit meaning, gate-delay reasoning, and physical interpretation when relevant.
- For CS / AI, retain architecture/process relationships and precise technical terms.

## Verification

After a meaningful multi-part edit:
1. fetch the page again;
2. confirm the new material is in the intended section;
3. confirm unrelated sections were preserved;
4. return the same Notion page link in chat.
