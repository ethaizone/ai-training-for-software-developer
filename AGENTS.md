# AGENTS.md — AI Training for Software Developers

This repo is a teaching guide. Purpose: help a senior software engineer who already
codes well but is new to AI-assisted development catch up fast. Primary stack:
opencode (AI harness) + DeepSeek (cheap, capable LLM). Secondary example: pi.dev.

## Audience & scope
- Reader: senior SE, solid practices, new to AI dev tooling. Do not re-explain coding.
- Primary stack: opencode + DeepSeek. Secondary: pi.dev.
- Language: plain, easy English (reader is a Thai native who reads English but not
  perfectly). No Thai. Short sentences, common words, active voice, no idioms.
- Curriculum (incremental order, this is the spine of the guide):
  1. opencode as an AI harness — what it is, install, the loop.
  2. DeepSeek as a cheap LLM — why cost matters, how to configure.
  3. Start coding with opencode — first session, driving the harness day-to-day.
  4. AGENTS.md as system instruction — making the agent follow your solution.
  5. Agent skills — packaging knowledge, workflows, and tools.
  6. MCP — using external data/tools. (Stance: creating MCP is hard; an agent
     skill is often the better choice. Teach this trade-off honestly.)

## Documentation rules

### Structure
- Organize markdown into folders by topic. One source of truth per topic.
- Each folder has a README.md index linking its pages.
- Top-level README.md is the master index with the recommended reading order.
- Prev/next navigation links at the bottom of every page.
- Cap each file at ~150–200 lines. When a file nears the cap, split it and
  cross-link. Keep it slim.

### Writing style
- Slim, lean, no redundancy. Keep detail, cut filler.
- No hype. State limitations directly.
- Lead with the mechanism (cause → effect in one sentence), then evidence.
- No ASCII art. Use Mermaid diagrams for visuals.
- Write long lines; let the editor soft-wrap. No fixed-column wrapping.

### Teaching approach
- Incremental mental model. Never assume prior AI knowledge.
- Every concept gets one concrete example — a real file, command, or config
  snippet — not abstract prose only.
- For agent/model behavior: explain why it fails there (probabilistic,
  context-bound) in one line, then how you/harness constrain it.
- End each module with a scannable cheat-sheet: do/don't + one snippet.

### Consistency & freshness
- One glossary (glossary.md). Define each AI term once (context window, tokens,
  tools/function-calling, MCP, agentic, system prompt, hallucination, RAG, …) and
  reuse. Link on first use.
- Date-stamp tool/model-specific advice ("as of YYYY-MM, opencode + DeepSeek").
  AI tooling rots fast; flag anything likely to age.

### Links
- Reference via links — never duplicate content across files.
- Recheck every link's liveness before calling any work done.

## Session logging
- This repo is itself a learning artifact. Log every session held here.
- At the end of each session, create `sessions/YYYY-MM-DD-slug.md` with:
  - **Goal** — what the user wanted.
  - **What happened** — key steps and decisions.
  - **Takeaways** — what a reader learns from this session.
- Use the current date from system context. `slug` = short kebab-case topic.
