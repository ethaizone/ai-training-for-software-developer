# Part 3 — Start coding with opencode

> **Goal:** install opencode, add a model, set up a safe permission system, and run your first session.
> **Keep this light.** opencode's commands and flags change. Tool advice here is dated **2026-07**. For anything deeper, read the official English docs: <https://opencode.ai/en/docs/>

## Install opencode

Pick one method. The install script is the simplest on macOS/Linux:

```bash
# macOS / Linux (install script)
curl -fsSL https://opencode.ai/install | bash
```

Other common options (full list on the docs home linked above):

```bash
# Node package managers
npm install -g opencode-ai     # or: bun / pnpm / yarn global
# Homebrew (macOS)
brew install anomalyco/tap/opencode
```

Check it works:

```bash
opencode --version
```

Then start it inside your project folder:

```bash
cd your-project
opencode
```

That opens the opencode interface right there in your terminal.

## Add a model

opencode does not ship with one locked-in model — you bring your own (see [Part 2](../02-deepseek/README.md) for why DeepSeek is a good default). The lightest way to start is to let opencode's `/models` command guide you through picking a provider and pasting an API key.

From inside opencode:

1. Type `/models` and pick a provider (for example, DeepSeek).
2. Paste your API key when asked (it is stored locally).
3. Pick the model you want as the default.

For repeatable setup you can also write it directly in your config file (next section shows the file). A typical entry looks like:

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "model": "deepseek/deepseek-chat"
}
```

> **Read the official models doc for the full, current list of providers and auth
> methods:** <https://opencode.ai/en/docs/models/>

## Set up the permission system (the important part)

This is where you make the [harness](../glossary.md#ai-harness) safe to leave running. opencode can read files, edit files, and run **any** shell command — so you must tell it what is allowed, what needs your approval, and what is blocked.

### The three states

Every action resolves to one of three states:

| State | Meaning |
|---|---|
| **`allow`** | Runs automatically, no prompt. |
| **`ask`** | Pauses and asks you before running. |
| **`deny`** | Blocked completely, never runs. |

### The whitelist concept (recommended)

Think in this order, not the reverse:

1. **Default to `ask`** for everything (`"*": "ask"`). Nothing runs without you.
2. **`allow` the safe, read-only commands** you use all the time (read a file, run tests, read-only git). These become friction-free.
3. **`deny` the dangerous commands** that should never run, even if asked (`rm -rf`, `sudo`, piping a download into a shell).

This is a **whitelist**: the model gets a small set of known-safe tools for free, asks before anything new, and is hard-blocked from the destructive stuff.

### A starter config

opencode loads config from `opencode.json` (or `opencode.jsonc`) — global at `~/.config/opencode/opencode.jsonc`, or per-repo at the project root. Here is a safe starter permission block (adapt to your own stack):

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "permission": {
    "edit": "allow",
    "bash": {
      "*": "ask",                 // default: ask for everything

      // --- safe, read-only → allow ---
      "ls *": "allow",
      "cat *": "allow",
      "grep *": "allow",
      "rg *": "allow",
      "find *": "allow",
      "git status*": "allow",
      "git diff*": "allow",
      "git log*": "allow",
      "git fetch*": "allow",
      "npm test*": "allow",
      "npm run build*": "allow",
      "npm run lint*": "allow",

      // --- dangerous → deny, always ---
      "sudo *": "deny",
      "rm -rf *": "deny",
      "rm /*": "deny",
      "curl *| bash*": "deny",    // block piping a download into a shell
      "wget *| bash*": "deny",    // (catch-all "ask" is the real backstop)
      "chmod -R 777 *": "deny"
    }
  }
}
```

How pattern matching works (from the official permissions doc):

- `*` matches zero or more characters. `"git *"` matches `git status`; bare `"git"` would not match arguments.
- Rules are matched in order, and **the last matching rule wins**.
- `edit: "allow"` here lets the model edit files freely; set it to `"ask"` if you want to approve every edit.

> **Full permission rules and syntax:** <https://opencode.ai/en/docs/permissions/>

## Run your first session

You are set up. Try a real task to feel the [loop](../01-opencode/README.md#what-is-an-ai-mode):

1. `cd` into a project and run `opencode`.
2. Describe a small, concrete task, e.g.: *"Find where the login error message is set and add the missing case for an expired password."*
3. Watch the loop: the model greps, reads files, proposes an edit, and may run a command.
4. When it hits a command that is not in your `allow` list, it **asks**. Approve safe steps; deny anything you do not want.
5. Review the final diff yourself before accepting.

The first session is the best teacher. You will quickly see which permissions you want to relax (too many `ask` prompts slows you down) and which you want to lock down.

---

## Cheat-sheet

**Do**
- Default to `ask`, `allow` the safe read-only commands, `deny` the destructive ones.
- Put `"*": "ask"` first; later rules override earlier ones.
- Start with a tiny real task to learn the loop.

**Don't**
- Don't default to `allow` and hope to catch the dangerous ones — that is backwards.
- Don't memorize flags; the docs move. Bookmark <https://opencode.ai/en/docs/>.

**One snippet** — the whitelist in one line:
> `ask` for everything → `allow` the safe few → `deny` the dangerous few. Order matters; last match wins.

---

[← Part 2: DeepSeek as a cheap LLM](../02-deepseek/README.md) · [↑ Index](../README.md) · [→ Part 4: The context window](../04-context-window/README.md)
