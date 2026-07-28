# Session 2026-07-28 — Build the six-part guide

## Goal
Turn the agreed rules into the actual teaching guide: six presentation-ready parts
covering opencode + DeepSeek, from "what is an AI harness" through to MCP. Each part
written, then reviewed by a subagent and fixed until clean. No private information
anywhere in the public guide.

## What happened
- **Researched before writing.** Verified current (2026-07) model names and pricing
  from vendor pages; verified every opencode doc URL, MCP doc syntax, skills format,
  AGENTS.md/rules discovery behavior, and both MCP examples (Context7, Chrome DevTools).
- **Built scaffolding:** master `README.md` index with a Mermaid reading-order diagram,
  and a `glossary.md` with real `##` headings (so anchors resolve).
- **Wrote each part, then ran a review-fix loop via subagent:**
  1. **opencode as harness** — fixed a Mermaid `Done?` node-id bug, a dead `[diff](#)`
     link, a `(Parts 4–6)` inaccuracy, added a concrete loop trace and a date-stamp.
  2. **DeepSeek** — the review caught a real math error (I wrote "10× cheaper"; the
     true figure is ~36× vs Sonnet 5, ~180× vs Opus 5). Corrected it, added a config
     snippet, removed idioms, kept the distillation framing honest and neutral.
  3. **Start coding** — fixed config correctness (`npm run build*` consistency, softened
     an over-promising curl-pipe deny comment), added the harness glossary link and a
     date-stamp, trimmed redundancy.
  4. **AGENTS.md** — small polish only (CLAUDE.md precedence wording, one redundancy).
  5. **Skills** — softened an MCP-context claim not backed by the skills doc source,
     removed "this is the magic" hype, added the missing MCP glossary link, de-duplicated.
  6. **MCP** — removed idioms ("rule of thumb", "reach for", "up front"), de-duplicated
     the cheat-sheet snippet.
- **Repo-wide final pass:** renamed a glossary heading (`Tools / function-calling` →
  `Tools and function-calling`) because the slash produced an unpredictable anchor;
  confirmed every glossary anchor now matches its heading, every intra-repo and
  external link resolves, no broken Mermaid, no private identifiers, all files within
  the 150–200 line cap.

## Takeaways
- **Review each part with a subagent before moving on.** The DeepSeek math error and
  the Mermaid node-id bug were both caught this way — exactly the failures a reader
  would lose trust over. The loop earned its cost.
- **Verify claims against the source you cite.** The skills-doc review flagged that an
  MCP behavior was stated as if the skills doc proved it. Tying each claim to its real
  source keeps the guide honest.
- **Anchors break silently.** A glossary built as a table has no linkable anchors, and
  a heading with a slash makes an unpredictable slug. Real `##` headings with simple
  names are the reliable choice — and a final repo-wide anchor check catches the rest.
- **Genericize from real configs.** The permission examples came from a real
  `opencode.jsonc`, but reduced to safe/dangerous *patterns* (deny `rm -rf`, allow
  read-only git) with no project names, keys, or paths — the teaching value without
  the privacy leak.

## Files created this session
- `README.md` (master index)
- `glossary.md`
- `01-opencode/README.md`
- `02-deepseek/README.md`
- `03-start-coding/README.md`
- `04-agents-md/README.md`
- `05-skills/README.md`
- `06-mcp/README.md`
