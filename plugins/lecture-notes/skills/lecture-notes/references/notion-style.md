# Notion Master Note Style

Load this reference when creating or reformatting the canonical lecture Master Note in Notion.

## Principle

The page should feel like a clean lecture handout / textbook note, not an AI dashboard and not a database dump.

Preserve content. Formatting should improve reading, scanning, and later editing.

## Default structure

- Use the page title for the lecture title; do not repeat the title as the first body heading.
- Use clear H1/H2/H3 hierarchy based on the actual knowledge structure.
- Use normal paragraphs as the default.
- Use bullet lists only for true enumerations.
- Use bold sparingly.
- Avoid decorative emoji in the body.
- Do not create columns, databases, toggles, or complex layouts unless they materially help or the user asks.

## Callout / highlight blocks

Use only a small number of native Notion callout/highlight blocks for content that already functions as:
- “记忆”
- “核心原则”
- “可以记成”
- a compact mental model
- a particularly important warning

Keep them visually quiet. Prefer neutral/light backgrounds and avoid turning every definition or example into a callout.

## AI explanation blocks

Answers inserted from Notion comments are part of the study note and should stay near the questioned text.

- Insert the answer immediately after the questioned paragraph/block when possible.
- Label it consistently as **AI 解释** or **学习解释**.
- Keep the styling distinct but restrained so the user can recognize it quickly.
- The user may select text inside these explanation blocks and ask another question.
- Follow-up answers should be inserted directly after the explanation being questioned.
- Do not automatically collapse, merge, or remove these blocks during ordinary cleanup.
- Only rewrite or remove them when the user explicitly asks.

## Formulas and technical material

- Preserve equations and mathematical notation.
- When Notion equation syntax is useful, follow the current Notion enhanced Markdown specification rather than guessing syntax.
- Keep compact process chains, mappings, truth tables, or short code snippets visually separated when this improves readability.

## Existing-note formatting rule

If the user says the existing content is already good and only wants formatting:
- do not rewrite;
- do not add new content;
- do not turn prose into bullets;
- do not add extra bolding;
- change only hierarchy, spacing/block choice, and a few justified callouts.
