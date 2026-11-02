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

The README is a single file with six sections, top to bottom:

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
- Forks with no commits of Leo's own on their default branch
  (`semantic-router`, `honcho`, `harness2`) — linking an unmodified fork reads
  as claiming someone else's work. A PR sent from a fork is listed under §4,
  via the upstream repo and the PR, never the fork.
- Repos whose commits use an email not linked to the account — GitHub shows
  no contribution record for them.

Currently eligible: `Grad-cam_FGSM` (sole author), `AI_Pet` (team project,
majority of commits). **Decision (2026-10-18):** Leo chose not to list
either — 2023 coursework would undersell the current focus.

**Listed:** `coevolve` — public, original, sole author, and the public
evidence for the self-evolution and meta-harness research. It was first listed
under an exception (2026-10-18) because its commits were authored under an
unlinked work email; they were re-attributed to the account on 2026-10-19, so
it now passes the rule outright.

Re-check eligibility before adding any other repo.

### 4. Open-Source Contributions
One top-level bullet per upstream repo (repo link + one-line description),
with one nested bullet per merged PR (PR link + what it fixed and why that
mattered).

**Eligibility rule:** a contribution may be listed only if the upstream repo
is public, the PR is **merged**, and the PR is authored by the `leo922oel`
account with its commits attributed to it. Open or closed-unmerged PRs are not
listed; add them once they merge. Link the upstream repo and the PR, never
the fork the PR was sent from (see §3).

**Listed (2026-11-02):** `google-research/harness2` — two merged fixes to the
JobBench OpenCode runner: #112 (per-rollout isolation of installs, temp files
and workspaces) and #122 (an `error` event in the trajectory when a rollout
exits non-zero). Both pass the rule: public repo, merged, authored and
committed as `leo922oel`. Listed because they are the public evidence for the
meta-harness research focus, on a framework built for exactly that.

**Listed (2026-11-02):** `vllm-project/semantic-router` — #5344 (merged
2026-10-22), a Dashboard fix that stops the Playground from adding the port
offset to an in-network Router target. Passes the rule the same way; listed
by Leo's decision as a merged fix to a widely used vLLM project. `harness2`
comes first because it backs the research focus.

### 5. Tech Stack (lightweight, text-only)
A single line of core skills separated by `·`, e.g.:
`Python · PyTorch · LLM / Agent frameworks · Context Engineering · Evaluation · System Architecture · Docker`
No image badges.

### 6. Connect
- LinkedIn badge linking to `https://www.linkedin.com/in/li-cheng-chien/`.

## Formatting Conventions

- Standard GitHub-Flavored Markdown only (renders reliably on the profile page).
- Center-aligned header is optional; default to left-aligned for simplicity.
- Keep total length short enough to read without scrolling on a laptop.
- Sections separated by `---` horizontal rules or clear headings.

## Open Items

- `google-research/harness2` #74 is open. Add it under §4 once it merges.

Resolved (2026-10-19): `coevolve` now has a repo description and is pinned.
Pinning replaced GitHub's auto-picked "Popular repositories", which had shown
`nachOS-Implementation`, a fork with no commits of Leo's own. Its commits were
re-attributed to the account by rewriting the author, so the §3 exception was
dropped.

## Success Criteria

- Renders correctly on the GitHub profile page.
- No broken links.
- Header, About, Research focus, Tech Stack, and Connect present; Featured Projects and
  Open-Source Contributions present only if they have eligible entries.
  Text-first, no heavy widgets.
- No private or contribution-less repo, and no unmerged PR, is referenced
  anywhere in the README source, including HTML comments.
- Leo can edit any section in under a minute without touching HTML.
