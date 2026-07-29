# Session 2026-07-29 — Add Part 13: parallel workspaces

## Goal
Add a third workflow section on **parallel workspaces** — how to run more than one AI
task at a time (build a feature while reviewing a colleague's PR) by giving each task its
own working directory, its own running stack, and its own AI session. Covers two repo
shapes (monorepo; many repos as a submodule folder) and the infrastructure isolation that
makes parallel *testing* possible (Docker Compose + a per-workspace project-name prefix +
overridable ports + shared infra).

## What happened
- **Planned before writing** (dogfooding Part 11). Proposed a one-sentence mechanism, a
  name, and an outline; got a confirm before building. Used this to surface the one
  ambiguity worth resolving up front — what "git worktree isn't solid" meant.
- **Naming.** User suggested "workspace development"; recommended **parallel workspaces**
  (mechanism-first, matches Parts 11/12). User agreed.
- **Resolved the worktree framing (reading a).** Worktree (or a second clone) supplies the
  extra directory but not the running stack — so it enables parallel *coding* but not
  parallel *testing*. The user's sharpened thesis became the spine of the part: a workspace
  is directory + running stack + AI session, and isolating the stack is the hard half.
- **Verified the one rotting fact before writing.** Read the primary source
  (https://docs.docker.com/compose/how-tos/project-name/): default project name = the
  directory that holds the compose file; the project name prefixes every container, network,
  and volume; `COMPOSE_PROJECT_NAME` overrides it. Cited the doc in the part.
- **Wrote Part 13** (79 lines, within cap) in the guide style: mechanism-first, a concrete
  two-workspace `docker compose` command, a Mermaid of two workspaces sharing infra, a
  cheat-sheet with the required one-line snippet, and cross-links to Parts 4/5/12.
- **Wired the spine:** master index table + reading-order Mermaid (node L), repo layout,
  the `AGENTS.md` curriculum (item 13), Part 12's footer next-link, and two glossary entries
  (`Workspace`, `Git worktree`).
- **Ran an independent fresh-context reviewer.** All Docker facts verified TRUE (precedence
  correct); links, Mermaid, privacy all clean. Four fixable findings, all addressed:
  - **Monorepo-vs-multirepo accuracy bug** (the reviewer's best catch): "default project
    name = folder name → isolation for free" is true for a monorepo but **false for the
    multi-repo case**, where the same repo folders repeat in every workspace and the
    default names collide. Reworded to cover both, and made `COMPOSE_PROJECT_NAME` the
    required override in the multi-repo case.
  - Unfulfilled Part 4 cross-ref → added a genuine context-window link in the body.
  - Missing cheat-sheet "one snippet" → added.
  - Idiom "side by side" → "at the same time"; plus "lives in / tears down" → plain wording.
- **Consistency sweep:** updated the now-stale "workflows group (Parts 11 and 12)" headers in
  Parts 11 and 12 to "(Parts 11–13)" so the group references stay correct.
- **Final checks:** 0 broken links, 0 missing glossary anchors, no remaining figurative
  `live/lives` in Part 13.

## Takeaways
- **The reviewer caught a real accuracy bug, not just style.** "Isolation for free" was
  true in one setup and false in the other — exactly the kind of half-truth an author stops
  seeing. Verifying the primary source *before* writing did not catch it; an independent
  reader applying the claim to the second scenario did. That is the Part 12 thesis again,
  proven on Part 13.
- **Resolve the framing ambiguity in the plan, not the draft.** Spending one round to
  confirm what "worktree isn't solid" meant shaped the whole section (worktree = the
  directory half; the stack is the teaching). Planning paid off more than any single edit.
- **Default behavior that "just works" hides a multi-repo trap.** Docker Compose's default
  project name is a convenience that becomes a collision when the same folder structure
  repeats across workspaces. Teaching *when the default breaks* is more valuable than
  teaching the default.
- **Renumber cost stayed zero.** Appending Part 13 to the `NN-workflows-*` run needed no
  spine renumber — only a new node, table row, layout line, curriculum item, and one
  next-link. The append-rather-than-insert decision from the last session kept paying out.
