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
  4. The context window — how messages accumulate turn by turn, why a full
     window causes drift, compacting between tasks, and how AGENTS.md and
     skills act as pre-loaded snapshots that save searching.
  5. AGENTS.md as system instruction — making the agent follow your solution.
  6. Agent skills — packaging knowledge, workflows, and tools.
  7. MCP — using external data/tools. (Stance: creating MCP is hard; an agent
     skill is often the better choice. Teach this trade-off honestly.)
  8. The feedback loop — keeping AGENTS.md and skills sharp over time.
  9. pi.dev — a leaner alternative harness (the secondary example). No permission
     system by design; teach the two safety practices (context hygiene, guardrails).
  10. Extending pi — extensions and hooks as pi's core design; the community
      packages that add MCP, sub-agents, and remote access.
  11. Workflows: plan and grill — write the plan to a file before you build,
      then grill every open decision into a recorded decision.
  12. Workflows: fresh-context review — spawn a clean subagent to review the
      work against the plan and the diff, looping until it finds nothing.

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

### Quality bar
- Verify every tool/model fact against its primary source before writing. AI
  tooling changes fast; never rely on memory for prices, model names, config
  syntax, or behavior. Cite the source (a doc URL is enough).
- No idioms, metaphors, or figurative speech. The reader is a Thai native —
  phrases like "rule of thumb", "price of admission", "the loop is the point"
  will confuse. Say it plainly.
- Glossary anchors must resolve. Build glossary entries as real `## Headings`
  with simple, punctuation-free names. Link to `glossary.md#slug` on first use.
- Mermaid only for diagrams (no ASCII art). Before finishing, check Mermaid
  syntax: node IDs must be alphanumeric (no `?`), labels with special chars
  must be quoted. If you set a node `fill`, also set a dark text `color`
  (e.g. `fill:#e8f0fe,color:#1a1a1a`) so it stays readable in dark mode.
- No private information anywhere in the guide — no names, handles, real
  project or repo names, real file paths, or API keys. When borrowing from a
  real config, keep the pattern, drop the identity. Public third-party
  resources (official docs, open-source skills and packages) may be linked
  as citations when they help the reader — this rule protects the author's
  own identity and configs, not external references.

### Consistency & freshness
- One glossary (glossary.md). Define each AI term once (context window, tokens,
  tools/function-calling, MCP, agentic, system prompt, hallucination, RAG, …) and
  reuse. Link on first use.
- Put one freshness stamp in the master README only ("Current as of YYYY-MM").
  Do not repeat it per part. AI tooling rots fast, so the parts that hold rotting
  facts (prices, model names, config syntax) should say "verify before relying" —
  but the date lives in one place.

### Links
- Reference via links — never duplicate content across files.
- Recheck every link's liveness before calling any work done.

## Workflow rules

### Review before done
- Every new or changed part must pass an independent review (a subagent or a
  human reviewer) against this AGENTS.md before it is considered done. The
  author does not self-approve.
- The reviewer checks: accuracy vs primary sources, idioms, redundancy, rule
  violations, dead links, broken Mermaid. Fix every finding before moving on.

### After every edit
- Re-read the lines around an edit before continuing. Edits can silently delete
  or shift adjacent content (e.g. swallowing a footer or a code fence).

## Session logging
- This repo is itself a learning artifact. Log every session held here.
- At the end of each session, create `sessions/YYYY-MM-DD-slug.md` with:
  - **Goal** — what the user wanted.
  - **What happened** — key steps and decisions.
  - **Takeaways** — what a reader learns from this session.
- Use the current date from system context. `slug` = short kebab-case topic.
