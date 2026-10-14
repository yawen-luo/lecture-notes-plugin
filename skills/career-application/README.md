# Career Application — Agent Skill

An English, evidence-grounded Agent Skill covering job-specific **resumes, academic CVs, cover letters, academic statements, independent application reviews, strict rubric scoring, and LaTeX formatting**.

This is **one skill with on-demand references**, not three conflicting agents. Load SKILL.md first, then open only the applicable reference:
- Cover letters: references/cover-letter.md
- Resume and CV: references/resume-cv.md
- Independent review and scoring: references/review-scoring.md
- Always: references/evidence-and-opportunity.md
- Requested formatting: references/format-and-templates.md
- Maintainer QA: references/test-cases.md

## Design priorities
1. **Evidence before claims.** No invented metrics, education, employment, publication or user tests.
2. **Job/program criteria before boilerplate.** Map real applicant contributions to the decision-maker's requirements.
3. **Reviewer independence.** Hard failures and documented weaknesses first; no self-congratulating rubric scores.
4. **Progressive disclosure.** One portable entry point with focused supporting references.
5. **Privacy-safe publication.** No raw personal evidence, transcripts, contact details, private documents or branded image assets in this directory.

## Assets

- assets/cover-letter-minimal.tex — reusable privacy-safe minimal letter skeleton
- assets/resume-jake-style.tex — privacy-safe Jake-style resume adaptation

The private source collection may contain a preferred original Jake Gutierrez template, a minimalist letter, and an optional SJTU-branded alternative. Fetch original assets from the user's authorized source when exact fidelity is requested. The public repository does not include private materials.

## Install

From a compatible Agent Skills CLI:

    npx skills add yawen-luo/lecture-notes-plugin --skill career-application

Validate locally using the Agent Skills reference validator when available:

    skills-ref validate skills/career-application

## Updating

Edit instructions in SKILL.md only for cross-document logic. Keep format-specific details in references/ and layout sources in assets/. Run test scenarios in references/test-cases.md, inspect changes for private material, then commit. Current skill version: **1.0.0**.

## Attribution

Uses the MIT license of the host repository. The "Jake-style" fallback was inspired by Jake Gutierrez's MIT-licensed resume template (https://github.com/sb2nov/resume), and is not a verbatim copy of the user's private template.
