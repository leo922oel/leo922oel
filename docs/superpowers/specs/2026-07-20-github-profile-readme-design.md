# GitHub Profile README — Design Spec

**Date:** 2026-07-20
**Author:** Leo (Li Cheng Chien)
**Target file:** `README.md` (the special `leo922oel/leo922oel` profile repo)

## Goal

Replace the default GitHub profile README with a clean, text-first,
professional-technical landing page that lets a recruiter or collaborator
understand who Leo is within ~15 seconds.

## Non-Goals (YAGNI)

- No animated typing SVGs, visitor counters, or trophy widgets.
- No heavy `github-readme-stats` dashboards or language-distribution cards.
- No large image-based tech-stack badge walls.

Rationale: low maintenance, never looks dated, keeps focus on substance.

## Audience & Positioning

- **Primary audience:** recruiters, research collaborators, open-source peers.
- **Positioning:** AI/LLM Architect · Researcher · Developer @ Delta Electronics.
- **Language:** English.

## Page Structure

The README is a single file with five sections, top to bottom:

### 1. Header
- `# Hi, I'm Leo (Li Cheng Chien) 👋`
- Subtitle line: `AI/LLM Architect · Researcher · Developer @ Delta Electronics`
- Location line: `📍 Taipei, Taiwan`

### 2. About / Experience
- One short intro paragraph (2–3 sentences).
- Bulleted research interests: LLM agents, model routing / Mixture-of-Models,
  MLOps, trustworthy AI.
- Draft copy provided by Claude; Leo edits to taste.

### 3. Featured Projects
Table or list, one line per project (title link + one-sentence description):
- `semantic-router` — System-level intelligent router for Mixture-of-Models
  (cloud / data center / edge).
- `honcho` — Memory library for building stateful agents.
- `Grad-cam_FGSM` — Trustworthy AI: adversarial robustness with Grad-CAM + FGSM.
- `AI_Pet` — ML team final project: AI pet.

Project links point to the corresponding GitHub repos. List is easy to edit.

### 4. Tech Stack (lightweight, text-only)
A single line of core skills separated by `·`, e.g.:
`Python · PyTorch · LLM / Agent frameworks · MLOps · Docker / Cloud`
No image badges.

### 5. Connect
- LinkedIn link with a `YOUR_URL` placeholder for Leo to fill in.

## Formatting Conventions

- Standard GitHub-Flavored Markdown only (renders reliably on the profile page).
- Center-aligned header is optional; default to left-aligned for simplicity.
- Keep total length short enough to read without scrolling on a laptop.
- Sections separated by `---` horizontal rules or clear headings.

## Placeholders Leo Must Fill

- LinkedIn URL (`YOUR_URL`).
- Confirm/adjust featured-projects list (some are forks).
- Confirm tech-stack line contents.

## Success Criteria

- Renders correctly on the GitHub profile page.
- No broken links (except intentional `YOUR_URL` placeholder).
- All five sections present, text-first, no heavy widgets.
- Leo can edit any section in under a minute without touching HTML.
