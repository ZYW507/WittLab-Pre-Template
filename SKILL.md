---
name: lab-report-ppt
description: 使用内置 PPT 模板，把用户提供的数据源（文本、图片、表格、链接或已有笔记）整理并填入 PPT。Use when the user wants Codex to create, update, or clean up a deck from provided materials using one of the bundled templates: InLab group report / weekly progress template or showreel script template, while strictly preserving the selected template style and avoiding redesign or invented content.
---

# Lab Report PPT Skill

## Goal

Convert the user's provided source material into a concise PPT using one bundled template.

Available templates and recommendation rules:

- `template/组会周报项目进展模板.pptx` - recommend for InLab group meeting reports, weekly reports, project progress updates, research progress, experiment progress, paper-writing progress, or supervisor feedback decks.
- `template/Showreel展示文稿模板.pptx` - recommend for showreel scripts, portfolio/project showcase copy, exhibition narration, demo video scripts, presentation storylines, or polished public-facing work summaries.

If the user's purpose clearly matches one template, recommend it briefly and proceed with that template. If the purpose is ambiguous, introduce both options in one short sentence and ask the user to choose one before generating the PPT.

This is a template-filling workflow. It is not a deck redesign workflow and not a report-planning workflow. Treat the user's data source as the only source of truth.

## Input Contract

Accept any user-provided data source, including:

- plain text, Markdown, notes, pasted paragraphs, or bullet lists;
- images, screenshots, diagrams, charts, or photos;
- structured data such as YAML, JSON, CSV, or tables;
- links or citations supplied by the user;
- an existing PPT that should be cleaned up using the template.

If the user provides enough material to proceed, do not ask extra planning questions. Ask only for missing files or essential information that cannot be inferred from the source, such as the presenter's name or date.

## Process

1. Inspect the source material and extract only explicit facts, claims, dates, people, deliverables, images, figures, citations, blockers, and next steps.
2. Condense the extracted material into slide-sized text. Prefer one sentence plus 2-4 short bullets per content area.
3. Map content to the closest matching template slide. Keep the existing template structure unless a slide is clearly irrelevant or the user asks for a specific page count.
4. Replace template/example text with the user's content. Do not introduce a new visual style.
5. Insert user-provided images only where the template already expects images or where an existing placeholder/image region can be reused.
6. Use `【待补充：字段名】` only for essential missing fields. Do not fabricate missing content to make the deck look complete.
7. Export a `.pptx` and verify that no old example text remains visible.

## Content And Style Rules

- Be concise. Remove filler, repeated context, and long note-style paragraphs.
- Keep the user's meaning and terminology. Lightly rewrite for clarity, but do not change claims.
- Keep every slide focused on one message.
- Prefer concrete wording from the source over generic phrases such as “持续推进”, “进一步优化”, or “完成相关工作”.
- Preserve references, figure captions, and image sources when the user provides them.
- If the source contains uncertainty, reflect it as uncertainty instead of turning it into a result.
- Preserve the template's layouts, typography, colors, page headers, footers, title hierarchy, spacing, image frames, tables, and page order.
- Do not create a new visual theme, add decoration, or redesign slides.
- Do not invent experiment numbers, results, citations, deadlines, author names, image sources, blockers, decisions, or future plans.

## Page Selection

Default to the smallest slide set that faithfully represents the provided material.

Use template slides as containers, not as a script that must always be fully populated:

- Keep title / overview slides when identity and topic information is available.
- Keep progress or key-work slides when the source describes work completed, learning progress, experiments, design iterations, writing progress, or implementation progress.
- Keep image/background slides only when the user provides or clearly references visual material.
- Keep blocker / decision slides only when the source includes blockers, risks, open questions, or requested feedback.
- Delete or leave unused slides out of the exported deck when they cannot be filled honestly.
- Add pages only when the user source requires more space; duplicate the closest matching template page and preserve its style.

## Final Check

Before finishing, check:

- the exported PPT still uses the original template style;
- no old example text remains visible;
- every factual claim comes from the user source or is marked `【待补充】`;
- images, citations, and data have source information when provided.
