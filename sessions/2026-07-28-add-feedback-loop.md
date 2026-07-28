# Session 2026-07-28 — Add Part 7: the feedback loop

## Goal
Add the missing practice the guide did not cover: `AGENTS.md` and skills are living
files that should be improved over time — by catching gaps and asking the agent itself
to update the instruction files. Decide where it lives, write it, review, fix.

## What happened
- **Decided placement.** The loop applies to *both* AGENTS.md (Part 4) and skills
  (Part 5), so it could not nest under either. Pasted into both would break the
  repo's own "one source of truth per topic" rule and the two copies would drift.
  Chose a new **Part 7** that closes the curriculum, with a one-line forward link
  from Parts 4 and 5.
- **Wrote Part 7** with the four-step loop (spot gap → explain fix → ask agent to
  update file → review diff), a Mermaid diagram of the cycle, two concrete examples
  (stale knowledge skill, narrow AGENTS.md rule), and the "corrected twice → file"
  trigger.
- **Updated the spine:** master index diagram + table now show Part 7; Part 6's
  footer gained a next-link; Parts 4 and 5 each got a short pointer to Part 7.
- **Reviewed via subagent, then fixed.** Review found no accuracy problems and all
  links valid, but flagged several idioms a Thai reader would miss ("hunting for it",
  "patched together", "found the hard way", "a blind copy") and a missing date-stamp.
  Also caught that an edit had accidentally deleted the footer links — restored.
  Fixed all of them.
- **Final verification:** every intra-repo link resolves, the Part 1 anchor
  `#what-does-not-change` matches its heading, forward links from 4/5/6/index to
  Part 7 are in place, Part 7 is 101 lines (within cap).

## Takeaways
- **A practice that spans two topics needs its own page.** One source of truth plus
  two short pointers beats duplicating the same content in two places — especially
  when the content will itself be edited over time.
- **The guide's own rules caught a structural mistake.** "Reference via links, never
  duplicate" (from AGENTS.md) is what stopped a same-content-in-both-files plan.
  Writing the rules first paid off a second time.
- **Idioms are the hardest writing rule to self-enforce.** Even after the first six
  parts, this part shipped with six of them. The review pass remains the reliable net.
- **Small edits can silently delete nearby content.** Replacing one paragraph removed
  the footer links; only re-reading the area caught it. The "read surrounding lines
  after each edit" habit from the global rules earned its cost here.
