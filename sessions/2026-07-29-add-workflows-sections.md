# Session 2026-07-29 — Add Parts 11–12: the workflows group

## Goal
Add two new sections on AI-coding **workflows**, grouped under a shared `workflows-`
prefix so more can be added later. Part 11 = **plan and grill** (write the plan to a
file, then grill the open decisions into a recorded decision). Part 12 = **fresh-context
review** (spawn a clean-window subagent to review the work against the plan + the staged
`git diff`, looping until it finds nothing, human takes the final decision).

## What happened
- **Planned before writing.** Presented a placement + naming + outline plan and got a
  one-word confirm before building — the very workflow Part 11 teaches.
- **Verified the grilling source before writing.** Read the real grilling skill: one
  question at a time, each with a recommended answer, walk the decision tree resolving
  dependencies one by one; look up facts, put decisions to the human; do not act until
  shared understanding. (The source link was added later — see the last bullet.)
- **Placed the two parts at the end (Parts 11–12), not mid-spine.** Workflows are
  harness-agnostic and build on everything before, so they work as a capstone. Appending
  also avoids renumbering the tail again, and an open-ended `1N-workflows-*` run means
  future workflows never force a renumber.
- **Named Part 12 "fresh-context review"** (over "side review"). It names the mechanism —
  the empty context window that gives an unbiased view — and ties straight to Part 4.
- **Wrote both parts** (Part 11 = 111 lines, Part 12 = 79 lines) in the guide's style:
  mechanism-first, a concrete `PLAN.md` skeleton, real `git diff --staged` snippet,
  Mermaid for both flows, cheat-sheets, and cross-links to Parts 4/5/6/10/11.
- **Wired the spine:** master index table + reading-order Mermaid (nodes 11–12), repo
  layout, the `AGENTS.md` curriculum (items 11–12), Part 10's footer next-link, and three
  new glossary entries (`Plan file`, `Decision record`, `Fresh-context review`).
- **Ran an independent fresh-context reviewer** (read-only subagent) per the guide's
  "review before done" rule. Verdict: all accuracy, Mermaid, links, anchors, redundancy,
  and privacy clean — CHANGES-NEEDED only on idiom/figurative items plus two logic slips.
- **Fixed every finding:** a goal-line self-contradiction ("grilling yourself" — but the
  *agent* grills *you*); an unfulfilled Part 5 cross-ref (dropped from "Builds on"); a
  missing Part 10→11 bridge; the idiom "make the final call" → "make the final decision"
  (5 spots); the figurative "loop until it is quiet" → "reports nothing" (part + index
  row); title terminology drift ("clean reviewer" → "fresh window"); and a figurative
  "building blocks" in my own bridge text.
- **Final checks:** 0 broken file links and 0 missing glossary anchors (script-verified);
  both parts within the cap.
- **Added the grilling skill link on request.** The user wanted learners to grab the real
  skill, so Part 11 now cites it directly. A public third-party citation is not the
  author's private info — so I also refined the privacy rule in `AGENTS.md` to allow
  external citations explicitly (it still protects the author's own identity and configs).
  Verified the link returns HTTP 200; 0 broken internal links.

## Takeaways
- **Two workflows that chain beat two standalone topics.** Part 11 produces `PLAN.md`;
  Part 12 reviews against it. Designing them as a producer/consumer pair made the
  cross-links load-bearing instead of decorative.
- **The reviewer caught a real logic error, not just style.** "Grilling yourself"
  contradicted the body (the agent grills you) — the kind of slip an author stops seeing.
  That is exactly the Part 12 thesis, proven on Part 11.
- **"Mechanism as the name" pays off.** Calling Part 12 "fresh-context review" (not "side
  review") makes the *why* self-explanatory for anyone who read Part 4 — the name does
  teaching work.
- **Append new categories; insert new foundations.** The costly renumber last session was
  for a *foundational* topic (context window) that had to sit mid-spine. These workflows
  are a *category* that will grow, so appending at `11–12-…` is future-proof: the next
  workflow just becomes Part 13 with zero renumber.
