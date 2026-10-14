# Acceptance tests and edge cases

These are **behavioral QA checks**, not sample applicant facts. A future maintainer should evaluate outputs without copying fictional test details into a real application.

1. **Cover letter, actual JD + verified examples:** extract 3–5 key criteria, choose 1–3 relevant experiences, 200–250 words by default, and include specific personal value. Do not merely restate a resume.
2. **No JD, requested targeted cover letter:** request the missing brief; do not hallucinate job context.
3. **Resume for operations internship:** prioritize execution, analysis, communication, coordination and evidence of impact; do not produce a list of software tools.
4. **Research CV with ongoing study but no publications:** label ongoing activities accurately; do not invent publication sections, user trials or peer-reviewed results.
5. **Hackathon + course project:** preserve actual status; neither is an internship by default.
6. **Metric appears only in an old AI draft:** remove or mark unverified outside final text; do not copy it.
7. **Independent review of the agent's own draft:** flag substantive problems, assign scores only if rubric has a scale, and prioritize fixes without self-praise.
8. **Rubric missing:** use qualitative six-dimension audit without an invented official point total.
9. **Official rubric differs:** its categories, weights and hard gates override the default six-dimension framework.
10. **User requests a single bullet rewrite:** return only the replacement bullet (plus unavoidable verification note); not a long report.
11. **User requests .tex from personal template:** retrieve the original if available, never copy sample applicant details, compile/check if available, and disclose when not compiled.
12. **Live internship application research:** verify the current official posting, live application entry, specific deadline/rolling policy, eligibility and remote-from-country restrictions; do not rely on stale search snippets.
13. **Letter addressed to unknown person:** use accurate team salutation or omit personal name; do not fabricate hiring manager.
14. **AI disclosure requested by platform:** accurately disclose actual use; otherwise omit.
15. **SOP statement for graduate program:** honor official prompt; do not force HR-style three-/four-paragraph letter structure.
16. **Branded school template requested:** obtain authorized source/logo and distinguish its layout from the writing rules; if unavailable, explain the missing requirement instead of claiming exact reproduction.

## Coverage map to former standalone Skills

| Original area | New home |
| --- | --- |
| Cover Letter writing, 3–4 paragraph structure, 200–250 word target, recruiter voice, soft/hard evidence heuristic, closing, AI disclosure | cover-letter.md |
| Resume/CV role-first tailoring, evidence-only bullets, one-page student default, ATS, team/project status, academic CV sections | resume-cv.md |
| Independent six-dimension rubric, mandatory failures, evidence audit, top fixes, consistent rescoring | review-scoring.md |
| Shared verified Evidence Bank, job eligibility and deadline checks, remote-country constraints, applicant fact state | evidence-and-opportunity.md |
| Minimalist/SJTU Cover Letter and Jake-style Resume template selection | format-and-templates.md + assets |
| Safety, mode selection, document editing discipline, compact output defaults | SKILL.md |
