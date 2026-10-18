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
- **Positioning:** AI/LLM Architect · Researcher · Developer @ Delta Electronics,
  building agentic system products.
- **Language:** English.

## Page Structure

The README is a single file with five sections, top to bottom:

### 1. Header
- `# Hi, I'm Leo (Li Cheng Chien) 👋`
- Subtitle line: `AI/LLM Architect · Researcher · Developer @ Delta Electronics`
- Location line: `📍 Taipei, Taiwan`
- One-line tagline as a blockquote.

### 2. About / Research focus
- About: the job title with years of experience (1.5); the two internal
  products (a coding agent and an AI coworker for knowledge work, 700+ users) and Leo's
  part in them (core agent runtime and module development); then one sentence
  on the work, with verbs in the subtitle's order (design → experiment →
  ship). No per-role breakdown: the subtitle already names the roles, and
  spelling each out reads as repetitive.
- "Research focus" bullets, one line each: memory, compaction, meta-harness,
  self-evolution, LLM-as-a-Judge.
- Draft copy provided by Claude; Leo edits to taste.

### 3. Featured Projects
Table or list, one line per project (title link + one-sentence description).

**Eligibility rule:** a repo may be listed only if it is public **and** carries
Leo's own contribution record on GitHub (commits attributed to the
`leo922oel` account). This excludes:
- Private repos.
- Forks with no commits of Leo's own (`semantic-router`, `honcho`) — linking
  an unmodified fork reads as claiming someone else's work.
- Repos whose commits use an email not linked to the account — GitHub shows
  no contribution record for them (see the `coevolve` exception below).

Currently eligible: `Grad-cam_FGSM` (sole author), `AI_Pet` (team project,
majority of commits). **Decision (2026-10-18):** Leo chose not to list
either — 2023 coursework would undersell the current focus.

**Exception (2026-10-18):** `coevolve` is listed by Leo's decision. It is
public and original, and it is the only public evidence of the self-evolution
and meta-harness research, but its commits are still authored as
`leo.lc.chien@deltaww.com`, which is not linked to the account. Once they are
re-attributed, the exception is no longer needed.

Re-check eligibility before adding any other repo.

### 4. Tech Stack (lightweight, text-only)
A single line of core skills separated by `·`, e.g.:
`Python · PyTorch · LLM / Agent frameworks · Context Engineering · Evaluation · System Architecture · Docker`
No image badges.

### 5. Connect
- LinkedIn badge linking to `https://www.linkedin.com/in/li-cheng-chien/`.

## Formatting Conventions

- Standard GitHub-Flavored Markdown only (renders reliably on the profile page).
- Center-aligned header is optional; default to left-aligned for simplicity.
- Keep total length short enough to read without scrolling on a laptop.
- Sections separated by `---` horizontal rules or clear headings.

## Open Items

- Re-attribute `coevolve`'s commits to the account (link the work email, or
  rewrite the author), so the §3 exception can be dropped.
- `coevolve` has no repo description; it shows empty on a pinned card.
- Profile page outside the README: with no pinned repos, GitHub's auto-picked
  "Popular repositories" shows `nachOS-Implementation`, a fork with no commits
  of Leo's own, which breaks the §3 rule. Pinning `coevolve` replaces that
  list. This is a GitHub settings change, not a README edit.

## Success Criteria

- Renders correctly on the GitHub profile page.
- No broken links.
- Header, About, Research focus, Tech Stack, and Connect present; Featured Projects present
  only if it has eligible entries. Text-first, no heavy widgets.
- No private or contribution-less repo is referenced anywhere in the
  README source, including HTML comments — the §3 `coevolve` exception aside.
- Leo can edit any section in under a minute without touching HTML.
