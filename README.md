# getexcited — Claude Code plugins

A small marketplace of Claude Code plugins by [Stefan Trockel](https://github.com/getexcited),
around one theme: agent verification, control and observability — knowing what
an agent is about to do, and being able to stop it.

```
/plugin marketplace add getexcited/claude-plugins
```

## Plugins

### [stepwarden](https://github.com/getexcited/stepwarden) · 0.1.0 · Apache-2.0

**Every tool call your agent makes, checked before it runs.**

Before a tool executes, stepwarden puts five independent questions to
[TypeSafe AI's Jev](https://typesafe.ai) — in parallel, against the session plan
and recent history — and lands the answer in one of three bands: allow it, ask
you, or block it and hand the reason back to the agent. Using a purpose-built
verification model instead of a full LLM review is what makes checking *every*
step affordable.

```
/plugin install stepwarden@getexcited
```

Requires Claude Code 2.1.273 or newer with `CLAUDE_CODE_ENABLE_FUNCTION_HOOKS=1`,
and a TypeSafe API key — the install dialog asks for one, and the plugin loads
and tells you what to do if you skip it.

> **Proof of concept.** It demonstrates an architecture pattern, its default
> thresholds have not been tuned on production traffic, and it is not a
> substitute for deterministic security controls. It installs in `mode: audit`:
> it logs every decision and blocks nothing until you run `/stepwarden enforce`.

See the [plugin README](https://github.com/getexcited/stepwarden#readme) for the
threat model, the full settings table, and what is and is not sent to TypeSafe.

## What this repo is

Only the catalog manifest — [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json).
No plugin code lives here; each entry points at its own repository. Claude Code
reads the manifest from the repository root and nothing else.

Validate a change before pushing:

```bash
claude plugin validate .
```

## License

Apache-2.0 — see [LICENSE](LICENSE). Each plugin carries its own license, listed
above and in its own repository.
