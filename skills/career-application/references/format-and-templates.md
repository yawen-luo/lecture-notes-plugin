# Formatting and template selection

Read when the user explicitly requests LaTeX, a template, exportable code/file, Word/PDF, a branded document or a layout review. **Content comes from verified evidence and target requirements; templates supply layout only.**

## Precedence and source access

1. Follow the **target employer/program's compulsory format**, exact question, page/word limits and filename requirements.
2. Follow an **explicit template chosen by the user**.
3. Otherwise use the applicant's established template preference if connected to the current work; request or retrieve its latest private source where needed.
4. Use a sanitized bundled fallback only if the original template cannot be obtained or the user prefers portable layout.

Never copy sample names, contact details, dates, Req IDs, fictional internships, authorships, publication claims or metrics into real application text.

## Resume / Academic CV LaTeX

For requests such as "my resume template" or "a one-page .tex resume", prioritize the user's existing **Jake Gutierrez resume layout** (the original or normalized version in the private Rubrics & Templates store), unless an alternate design or target format was requested. Preserve the recognizable custom commands, section style and structure, but choose actual sections according to the target JD and evidence, not the sample's list of headings.

Available local fallback: [resume-jake-style.tex](../assets/resume-jake-style.tex). This is a privacy-safe **adaptation** inspired by the MIT-licensed Jake Gutierrez template, not a claim to reproduce the user's exact private source bytes. If exact fidelity matters, retrieve the user's approved original LaTeX source instead. The published upstream reference is https://github.com/sb2nov/resume (MIT license).

Usual sections as warranted: Header/Contact, Education, Relevant Coursework, Experience/Research, Projects, Technical Skills, Leadership/Extracurricular, Awards. Default to one-page student resume. Academic CV may exceed one page with appropriate content; do not reduce factual accuracy to meet an arbitrary template.

Check consistency, line wrapping, potential overfull text, genuine ATS-readable text, correct Unicode/PDF mapping, compile logs and final visual page count **when tools are available**. If compilation was not executed, do not say it succeeded.

## Minimalist Cover Letter LaTeX

Default to the user's **minimalist cover-letter layout** for LaTeX requests unless another official/user layout is specified:
- Centered uppercase name.
- Two-column contact band: phone/email at left, confirmed postal/location details at right.
- Thin horizontal rule underneath.
- Date, recipient/team and confirmed address if actually needed, professional greeting.
- Three or four meaningful body paragraphs, closing, signature/print space and enclosure **only when actual attachments exist**.
- Approximately 0.75-inch top/bottom and 1-inch left/right margins; normally 10–11pt in a standard LaTeX letter class. General readability should be 10–12pt according to recipient requirements. Single-page final layout where appropriate.

Available sanitized fallback: [cover-letter-minimal.tex](../assets/cover-letter-minimal.tex). Do not use a nonstandard 10.5pt option with the standard LaTeX letter class without explicitly confirming the class supports it. An original historical sample used 10.5pt; that is not proof it compiles.

The original historical letter included unverified publication claims, metrics, a dated job identifier and mailing details. None are part of this Skill's applicant evidence. Replace everything with verified current inputs. Do not add "Enclosure: Resume" if not really attached.

## Optional SJTU-branded letter

An **opt-in** historical SJTU-branded 2023 LaTeX source exists in the user's private template collection; it uses an article document class, Charter font, A4 with one-inch margins, a header image, horizontal rule and a footer rule. Select it **only** when the user specifically asks for the SJTU-branded/official-looking stationery or supplies this template. It does not supersede the minimalist default. Do not present the sample as an officially endorsed university template.

The original compilation assumes a matching logo file named sjtu.png beside template.tex. This public Skill intentionally does **not** ship a university logo, historical personal statement, contact data or private attachment. For actual use, obtain the authorized source and image from the user/private template, verify permission and attribution, then confirm final rendering and page count. Do not assert the online logo copy is byte-identical to the user's original image.

## Practical output discipline

- If asked only for wording, do **not** create TeX/PDF/DOCX files.
- If asked for editable TeX, provide a true compilable source with all placeholders explicitly resolved or marked draft, not invented personal information.
- If asked for a PDF/DOCX, use appropriate document tooling and check the result rather than substituting a screenshot or a sample template.
- Email applications may require a subject line instead of full printed letter stationery.
- Version naming suggestion: YYYY-MM-DD_Company_Role_Type_vN, where Type is Resume/CV/CL/Review. Log meaningful changes, input sources and unresolved facts. Keep one canonical fact bank; store job-specific drafts separately.
