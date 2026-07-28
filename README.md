# AI Training for Software Developers

A lean guide for senior software engineers who already code well but are new to
AI-assisted development. You will learn how to drive an **AI harness** so the model
follows your solution, instead of the other way around.

> **Stack:** [opencode](https://opencode.ai/) (the harness) + DeepSeek (a cheap, capable LLM).
> **Current as of 2026-07.** AI tooling changes fast — prices, model names, and config syntax may have shifted since then. Verify before relying on specifics.

## Who this is for

You are a senior software engineer. Your practices are solid. You do not need to be
taught how to code. You want AI as a tool that assists you — and you want to know
how to make the model follow your solution when it is not great on its own.

## How to read this guide

Read in order. Each part builds on the one before. Every part ends with a short
**cheat-sheet** you can scan. Unfamiliar words are defined once in the
[glossary](glossary.md) and linked on first use.

```mermaid
flowchart LR
    A["1. opencode<br/>the harness"] --> B["2. DeepSeek<br/>the model"]
    B --> C["3. Start coding<br/>drive it"]
    C --> D["4. AGENTS.md<br/>rules"]
    D --> E["5. Skills<br/>knowledge & tools"]
    E --> F["6. MCP<br/>external data"]
    D -.-> G["7. Feedback loop<br/>keep instructions sharp"]
    E -.-> G
    style A fill:#e8f0fe,color:#1a1a1a
    style G fill:#e6f4ea,color:#1a1a1a
```

## Contents

| # | Part | What you learn |
|---|------|----------------|
| 1 | [opencode as an AI harness](01-opencode/README.md) | What a harness is, why it beats chatting to a model, how it changes your day. |
| 2 | [DeepSeek as a cheap LLM](02-deepseek/README.md) | Why cost matters, how DeepSeek compares, the truth about "Chinese models". |
| 3 | [Start coding with opencode](03-start-coding/README.md) | Install, add a model, set up safe permissions, run your first session. |
| 4 | [AGENTS.md as system instruction](04-agents-md/README.md) | Make the agent follow your solution. Global vs repo rules. |
| 5 | [Agent skills](05-skills/README.md) | Package knowledge, workflows, and tools the agent can pick on its own. |
| 6 | [MCP — when to use it](06-mcp/README.md) | Plug in third-party data/tools. Why a skill is usually the better choice. |
| 7 | [The feedback loop](07-feedback-loop/README.md) | Keep AGENTS.md and skills sharp over time, using the agent to update them. |

## Repo layout

```
AGENTS.md            ← rules for writing this guide (read this first if you contribute)
README.md            ← this file (master index)
glossary.md          ← AI terms, defined once
01-opencode/         ← Part 1
02-deepseek/         ← Part 2
03-start-coding/     ← Part 3
04-agents-md/        ← Part 4
05-skills/           ← Part 5
06-mcp/              ← Part 6
07-feedback-loop/    ← Part 7
sessions/            ← logs of real sessions (learning artifacts)
```

---

[→ Start with Part 1: opencode as an AI harness](01-opencode/README.md)
