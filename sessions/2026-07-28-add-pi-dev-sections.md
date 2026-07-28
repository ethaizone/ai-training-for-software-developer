# Session 2026-07-28 — Add Parts 8–9: pi.dev and extending pi

## Goal
Add the guide's secondary example: **pi.dev** as a second harness. The user gave
several points to cover — pi is leaner than opencode, has no permission system (so it
runs every command without asking), needs two safety habits (keep context lean, use a
guardrail), has a strong extension/hook system, lacks native MCP and sub-agents (fill
those with community packages), and can be driven from Telegram when away from the desk.

## What happened
- **Verified every claim against a primary source before writing.** Read pi's bundled
  docs (README, `docs/security.md`, `docs/extensions.md`). They confirm the core points:
  pi "does not include a built-in sandbox"; tools run "with the permissions of the pi
  process"; philosophy lists "**No MCP**", "**No sub-agents**", "**No permission
  popups**"; the `tool_call` hook "can block" and `tool_result` "can modify"; "pi can
  create extensions. Ask it to build one." Also confirmed pi shows context usage in the
  footer and has auto-compaction plus `/compact` — both support the context-hygiene habit.
- **Confirmed the four community repos are real and do what the user said** (web search):
  `aliou/pi-guardrails` (security hooks), `nicobailon/pi-mcp-adapter` (token-efficient
  MCP — proxies many tools through one ~200-token tool), `nicobailon/pi-subagents`
  (delegate to child agents), `llblab/pi-telegram` (drive pi from a Telegram DM).
- **Decided on two parts, not one.** The content was too large for the ~200-line cap, and
  it splits cleanly: **Part 8** = pi as a harness + the no-permission trade-off + the two
  safety practices; **Part 9** = extensions/hooks + the ecosystem packages. This also
  mirrors how the guide treats opencode (a part for the harness/permissions, separate
  parts for skills/MCP).
- **Connected pi back to the existing guide** so the mental model carries over: pi loads
  `AGENTS.md` (Part 4) and has the same skills standard (Part 5), and supports DeepSeek
  (Part 2). A comparison table shows what each harness ships by default.
- **Updated the spine:** master index table, the reading-order Mermaid (new nodes 8–9),
  repo layout, the curriculum list in `AGENTS.md`, Part 7's footer (gained a next-link),
  and two new glossary entries (`Extension`, `Hook`).
- **Ran an independent subagent review** (read-only, fresh context) per the guide's
  "review before done" rule. Verdict: all 10 accuracy claims verified against primary
  sources, no blockers. Four SHOULD-FIX style issues and some NITs.
- **Fixed every SHOULD-FIX and the clear NITs:** a figurative phrase ("bottomless
  buffer"), an idiom ("bolt on a guardrail"), hype words ("unusually powerful", "very
  deep", "more power"), a redundant phrase ("from scratch by hand"), a link that pointed
  at the pi home page but was labelled "extensions doc" (repainted to the real doc URL),
  and two mild figurative words ("buried", "sharp"). Left the repo-wide hard-wrapping
  alone: every file including `AGENTS.md` uses it, so matching it is the consistent
  choice, not a new defect.
- **Final checks:** Part 8 = 129 lines, Part 9 = 109 lines (both within cap); every
  intra-repo and glossary link resolves; Mermaid is compliant (alphanumeric IDs, quoted
  labels, `fill` always paired with a dark `color`); freshness date appears only in the
  master README, not in the new parts.

## Takeaways
- **Verify against the primary source first, then write.** The user's claims were all
  correct, but stating them as facts without checking would have broken the guide's own
  quality bar. Reading pi's docs also surfaced the features that make the user's safety
  habits concrete (footer context meter, `/compact`) — material the bare prompt did not
  mention.
- **The config-vs-code contrast is the clean way to explain two harnesses.** "opencode's
  safety is config (you write rules); pi's is code (you write a hook)" turns a list of
  differences into one mechanism the reader can hold.
- **pi-mcp-adapter ties two parts together.** Its "proxy many MCP tools through one
  compact tool" design is a direct answer to Part 6's "MCP loads the full tool list into
  context" cost — and to Part 8's context-hygiene habit. Linking that made the ecosystem
  table echo the guide's earlier points instead of repeating them.
- **The idiom/hype net still catches things the author misses.** "Bolt on", "bottomless",
  "unusually powerful" all passed the first draft. The independent review is the reliable
  catch, exactly as the rules intend.
