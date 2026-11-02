# GitHub Profile README Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the default `README.md` with a clean, text-first professional-technical GitHub profile landing page.

**Architecture:** A single `README.md` at repo root using standard GitHub-Flavored Markdown. Six stacked sections (Header, About + Research focus, Featured Projects, Open-Source Contributions, Tech Stack, Connect). No external widgets, scripts, or images beyond one LinkedIn badge.

**Tech Stack:** GitHub-Flavored Markdown only.

**Spec:** `docs/superpowers/specs/2026-07-20-github-profile-readme-design.md`

## Global Constraints

- Standard GFM only — must render on the GitHub profile page (no raw HTML that GitHub strips, no external JS).
- Text-first: no animated SVGs, visitor counters, trophy widgets, or `github-readme-stats` cards.
- No image-based tech-stack badge walls; tech stack is one plain-text line.
- Language: English.
- **Repo eligibility:** reference a repo — in links, text, or HTML comments — only if it is public **and** carries Leo's own contribution record on GitHub (commits attributed to `leo922oel`). Excluded today: all private repos; `semantic-router`, `honcho` and `harness2` (forks with no own commits on their default branch).
- **Contribution eligibility:** list a PR to someone else's repo only if the repo is public, the PR is merged, and it is authored by `leo922oel` with commits attributed to the account. Link the upstream repo and the PR, never the fork. Listed (2026-11-02): `google-research/harness2` #112 and #122; `vllm-project/semantic-router` #5344.
- **Featured:** `coevolve` — passes the rule since its commits were re-attributed to the account (2026-10-19); it was listed under an exception before that.
- **Coursework not listed:** `Grad-cam_FGSM` and `AI_Pet` pass the rule but are 2023 coursework; Leo chose not to list them (2026-10-18).

---

### Task 1: Write the profile README

**Files:**
- Modify: `README.md` (was the GitHub default template)

**Interfaces:**
- Consumes: profile facts — name "Li Cheng Chien" (Leo), role "AI/LLM Architect · Researcher · Developer @ Delta Electronics", location "Taipei, Taiwan", 1.5 years of industry experience, two internal products (a coding agent and an AI coworker for knowledge work, 700+ users) where Leo owns the core agent runtime and module development, LinkedIn `https://www.linkedin.com/in/li-cheng-chien/`.
- Produces: the final rendered profile page. No downstream code consumes this.

- [x] **Step 1: Replace `README.md` with the final content**

`README.md` itself is the source of truth for the wording. Sections, top to bottom:

1. Header — name, role line, location, one-line tagline blockquote.
2. About — job title with years of experience, the two internal products and Leo's part in them, and one sentence on the work (design → experiment → ship); then "Research focus": memory, compaction, meta-harness, self-evolution, LLM-as-a-Judge.
3. Featured Projects — `coevolve`.
4. Open-Source Contributions — `google-research/harness2` (PRs #112 and #122) then `vllm-project/semantic-router` (PR #5344), one nested bullet per PR.
5. Tech Stack — `Python · PyTorch · LLM / Agent frameworks · Context Engineering · Evaluation · System Architecture · Docker`
6. Connect — LinkedIn badge.

> Note: the single LinkedIn badge is the one exception to "no badges" — it is a
> conventional, static link affordance, not a stats/widget wall. If Leo prefers
> plain text, replace with `[LinkedIn](https://www.linkedin.com/in/li-cheng-chien/)`.

- [x] **Step 2: Verify the repo-eligibility rule**

Run:
```bash
# Every repo linked from the README must be public and carry commits from leo922oel
for r in $(grep -o 'github.com/leo922oel/[A-Za-z0-9_.-]*' README.md | cut -d/ -f3 | sort -u); do
  priv=$(gh api "repos/leo922oel/$r" --jq '.private')
  own=$(gh api "repos/leo922oel/$r/commits?author=leo922oel&per_page=1" --jq 'length')
  if [ "$priv" = false ] && [ "$own" -gt 0 ]; then echo "ok: $r"; else echo "FAIL: $r (private=$priv own_commits=$own)"; fi
done
# Every PR linked from the README must be merged and authored by leo922oel
for p in $(grep -o 'github.com/[A-Za-z0-9_.-]*/[A-Za-z0-9_.-]*/pull/[0-9]*' README.md | sort -u); do
  repo=${p#github.com/}; repo=${repo%/pull/*}; n=${p##*/}
  gh api "repos/$repo/pulls/$n" --jq "if .merged and .user.login == \"leo922oel\" then \"ok: $repo#$n\" else \"FAIL: $repo#$n (merged=\(.merged) author=\(.user.login))\" end"
done
# Every upstream repo linked from the README must be public
for r in $(grep -o 'github.com/[A-Za-z0-9_.-]*/[A-Za-z0-9_.-]*' README.md | grep -v '/leo922oel/' | cut -d/ -f2,3 | sort -u); do
  gh api "repos/$r" --jq 'if .private then "FAIL: \(.full_name) is private" else "ok: \(.full_name) public" end'
done
# Excluded forks must not appear anywhere, including comments
grep -nEi 'leo922oel/(semantic-router|honcho|harness2)' README.md || echo "clean: no excluded repos"
# Private repo names must not appear. -w is required: a private repo named
# "OS" would otherwise match inside "Most" / "across".
gh api "user/repos?visibility=private&affiliation=owner&per_page=100" --jq '.[].name' \
  | grep -niwFf - README.md || echo "clean: no private repos"
```
Expected: the repo loop prints `ok: coevolve`; the PR loop prints `ok:` for `google-research/harness2#112`, `#122` and `vllm-project/semantic-router#5344`; the upstream loop prints `ok: ... public` for both upstream repos; no `FAIL` line appears; and the last two commands print their `clean:` line. After adding any repo or PR later, run this step again.

- [x] **Step 3: Confirm no forbidden elements**

Run:
```bash
grep -nEi 'readme-stats|githubusercontent.*streak|typing-svg|profile-views|trophy' README.md || echo "clean: no heavy widgets"
```
Expected: prints `clean: no heavy widgets`.

- [x] **Step 4: Commit**

Two commits, each confirmed by Leo before running (per git-workflow policy):
1. `README.md` — the profile page itself.
2. Spec + this plan — the eligibility rule, the `coevolve` exception, and the decision not to list coursework.

Do NOT push (Leo pushes manually).

---

## Self-Review

- **Spec coverage:** Header ✓, About / Research focus ✓, Featured Projects (`coevolve`) ✓, Open-Source Contributions (`harness2` #112, #122; `semantic-router` #5344) ✓, Tech Stack line ✓, Connect / LinkedIn ✓.
- **Placeholder scan:** none left — LinkedIn URL is filled in.
- **Eligibility:** the only own repo linked is `coevolve`, which passes the rule; the three linked PRs are merged and authored as `leo922oel`. Step 2 checks every linked repo and PR, so it guards future edits.

## Post-Implementation Checklist for Leo

- [x] Fill in the LinkedIn URL.
- [x] Adjust the About wording.
- [x] Decide on Featured Projects — `coevolve` listed; coursework not listed (2026-10-18).
- [x] Commit as the personal account (`leo922oel@gmail.com`) so this repo's
      commits earn a contribution record; the earlier spec commit was
      re-authored before push.
- [x] Confirm commit messages, then commit (README first, then spec + plan).
- [x] Push to `main` to publish the profile page.
- [x] Add a repo description to `coevolve` (2026-10-19).
- [x] Pin `coevolve` (2026-10-19). This replaced GitHub's auto-picked
      "Popular repositories", which had shown `nachOS-Implementation`, a fork
      with no commits of Leo's own.
- [x] Re-attribute `coevolve`'s commits to the account (2026-10-19): the
      author was rewritten to `leo922oel@gmail.com` and force-pushed, so the
      exception was dropped.
- [x] List the two merged `google-research/harness2` PRs (#112, #122) under
      Open-Source Contributions (2026-11-02).
- [x] List `vllm-project/semantic-router` #5344 (merged 2026-10-22) under
      Open-Source Contributions (2026-11-02).
- [ ] Add `google-research/harness2` #74 once it merges.
