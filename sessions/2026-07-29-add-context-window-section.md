# Session 2026-07-29 — Add Part 4: the context window

## Goal
Add a new section explaining the **context window**: how messages accumulate turn by
turn (system prompt + `AGENTS.md` + each user message, model reply, and tool result),
why a nearly full window causes drift and hallucination, the compaction habit (compact
after each big task; opencode's auto-compact is unreliable in practice), and how
`AGENTS.md` and skills act as pre-loaded snapshots that cut context usage by saving the
model from scanning code or fetching docs.

## What happened
- **Verified the opencode facts against primary sources before writing.** Read the
  official config doc: `compaction.auto` defaults to `true` and compacts **"when the
  context is full"** (i.e. at 100%, already past the ~90% quality-drop zone — the
  precise reason auto-compact feels unreliable). Confirmed `/compact` (alias
  `/summarize`) and the `prune` / `reserved` options from the config and TUI docs, and
  that compaction is lossy. Community reports that the default algorithm is weak match
  the user's experience.
- **Placed it as Part 4, between "Start coding" (3) and "AGENTS.md" (now 5).** Reasoning:
  the reader has just run a first session and watched messages pile up, so compaction
  advice lands; and the section's "snapshots not searching" insight directly motivates
  the AGENTS.md and skills parts that follow.
- **Renumbered the whole tail of the spine** (folders `04`–`09` → `05`–`10`) and fixed
  every cross-reference so the numbered-folder convention stays honest: master index
  table, the reading-order Mermaid (new node 4), repo layout, the curriculum list in
  `AGENTS.md`, all prev/next footers, every in-body `Part N` pointer, and the glossary
  `[→ Part N]` links (plus a new Part-4 link on the `Context window` glossary entry).
  Used plain `mv`, not `git mv`, to leave the index untouched per the repo's git rules.
- **De-duplicated the pi part.** `09-pi`'s "Practice 1: keep the context window lean"
  used to re-explain the mechanism and the 90% rule. Trimmed it to defer to Part 4 and
  keep only the pi-specific bits (footer usage meter, `/compact`), per the "never
  duplicate content across files" rule.
- **Left the 2026-07-28 session logs untouched.** They are point-in-time records that
  name the old part numbers ("Add Part 7: the feedback loop", etc.). Rewriting them to
  the new numbering would falsify history; the renumber is documented here instead.
- **Ran an independent reviewer subagent** (fresh context, read-only) per the guide's
  "review before done" rule. Verdict: all accuracy claims verified against primary
  sources, all links/anchors resolve, structure and Mermaid compliant — CHANGES-NEEDED
  only on idiom/metaphor violations.
- **Fixed every review finding:** "something has to give", "the bigger lever", "burns a
  chunk of the window", "seam between tasks", and "bulk up" → plain wording; fixed a
  muddled Mermaid edge label (`keeps growing` → `reached`); added a first-use
  `[tokens]` glossary link; and reconciled the "rules live at the top" / "rules lose
  weight" wording into one consistent phrasing.
- **Final checks:** an automated pass found **0 broken internal links**; Part 4 = 97
  lines (within cap); all 10 folders present and correctly ordered; Mermaid compliant.

## Takeaways
- **Inserting a foundational topic mid-spine costs a full tail renumber.** The numbered
  folders *are* the reading order, so there is no shortcut — placing "context window" at
  Part 4 meant renumbering 04–09 and auditing every `Part N` reference. The link-liveness
  script is what made this safe to verify at scale.
- **"Auto-compact fires when full" is the mechanism behind "unreliable."** The user's
  lived experience maps to a precise cause: it triggers at 100%, past the ~90% zone where
  the model already drifts. Stating the cause turns a complaint into a fix (compact
  yourself, between tasks).
- **"Snapshots not searching" is a fresh frame for AGENTS.md and skills.** It reframes
  them as a context-economy move — a few hundred tokens once, instead of thousands of
  tokens of grepping and doc-fetching every session — which sets up Parts 5–6 better than
  the "rules the model follows" framing alone.
- **The idiom ban catches what a native speaker misses.** Five phrases ("something has to
  give", "bigger lever", "burns a chunk", "seam", "bulk up") passed the first draft. The
  independent review is the reliable net, exactly as the rules intend.
