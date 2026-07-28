# Session 2026-07-28 — Set up the guide's rules

## Goal
Define how this teaching guide works before writing any content. The repo is a
guide for senior software engineers who code well but are new to AI-assisted
development. We needed to lock the conventions first, then build on them.

## What happened
- Started from an empty repo (no files, no commits, no remote).
- Agreed the realistic way to "log every session" is an agent convention, not
  built-in tooling: at session end, the agent writes a structured file here.
- Picked the scope through four questions:
  - **Tool scope** → opencode primary, pi.dev secondary (later refined: opencode
    + DeepSeek as the primary stack).
  - **Session logs** → one file per session in `sessions/`.
  - **Language** → plain English only, no Thai.
  - **Curriculum entry** → start from the paradigm shift, not LLM basics or
    prompt engineering.
- Refined the curriculum from a broad sketch to a focused, opencode-centric spine:
  opencode harness → DeepSeek (cheap LLM) → start coding → AGENTS.md → agent
  skills → MCP (with the honest stance that skills often beat building an MCP).
- Adjusted two rules to match: softened "concrete example" to a real file/command/
  config snippet (no deep prompt/payload mechanics), and baked the curriculum
  spine into AGENTS.md.
- Wrote `AGENTS.md` at the repo root. Stopped there, before building the guide.

## Takeaways
- **Lock conventions before content.** Spending a session on rules means the guide
  stays consistent as it grows, and later files don't drift apart.
- **Session logging is a convention, not magic.** No tool auto-dumps a session.
  The value comes from the agent writing Goal / What happened / Takeaways at the
  end — that summary is the learning artifact, more than a raw transcript would be.
- **Pick the primary tool early and teach through it.** A senior SE learns the
  new layer fastest by seeing concepts in the one tool they'll actually use.
- **Be honest about tool limits in the guide itself.** The MCP-vs-skills stance is
  taught as a trade-off, not a rule — modeling the no-hype tone the guide asks for.
