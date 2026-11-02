# Hi, I'm Leo (Li Cheng Chien) 👋

### AI/LLM Architect · Researcher · Developer @ Delta Electronics

📍 Taipei, Taiwan

> I build agentic systems that still work on the hundredth task, not just the first.

---

## About

I'm an AI/LLM Architect at Delta Electronics with 1.5 years of industry
experience. I'm responsible for the core agent runtime and module development
of two internal products used by 700+ employees: a coding agent and an AI
coworker for knowledge work. I design how agents, tools, models, and data fit
together, run experiments on the core modules listed below, and ship what
holds up into production.

## Research focus

- 🧠 **Memory** — what an agent keeps across sessions, and how it recalls the right piece at the right time
- 🗜️ **Compaction** — condensing long-running context without losing the facts a task depends on
- 🧩 **Meta-harness** — tuning the harness around the model (prompts, tools, context policy) instead of the model itself
- 🔁 **Self-evolution** — agents that turn their own run history into lasting improvements
- ⚖️ **LLM-as-a-Judge** — evaluating agent output with models, and checking that the judge itself can be trusted

---

## Featured Projects

- **[coevolve](https://github.com/leo922oel/coevolve)** — self-evolution and meta-harness in practice: a feedback loop for Claude Code that turns session history into lessons, enforces them as hooks, rules, or skills, and measures whether behaviour actually changed

---

## Open-Source Contributions

- **[google-research/harness2](https://github.com/google-research/harness2)** — Harness², a framework for recursive agent harnessing; two merged fixes to its JobBench rollout runner:
  - [#112](https://github.com/google-research/harness2/pull/112) — isolate each rollout's installs, temp files and workspace, so state leaked between rollouts can't pass for a harness edit's effect
  - [#122](https://github.com/google-research/harness2/pull/122) — note in the trajectory when a rollout times out or is killed, so a cut-off run no longer reads as a finished one
- **[vllm-project/semantic-router](https://github.com/vllm-project/semantic-router)** — a programmable decision layer for models and compute; one merged fix to its Dashboard:
  - [#5344](https://github.com/vllm-project/semantic-router/pull/5344) — stop the Playground from adding the port offset to an in-network Router target, which made every request on an offset stack fail with 502

---

## Tech Stack

Python · PyTorch · LLM / Agent frameworks · Context Engineering · Evaluation · System Architecture · Docker

---

## Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/li-cheng-chien/)
