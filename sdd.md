Describe the codebase's business logic in `SPEC.md` files, placed beside the code that implements it:
- `some-dir/` => `some-dir/SPEC.md`
- `some-file.ext` => `some-file.SPEC.md`

# Goal

A `SPEC.md` is the answer a human gives when a colleague asks "how does this work?" — the high-level business logic, nothing else.

Litmus test: every sentence must be one you'd *say out loud* when explaining how it works. Sentences about the repository itself (build, CI, release, packaging, tooling) or about code mechanics (libraries, flags, clever tricks) fail the test — that's how the repository works, not how the product works.

- Humans reason top-down (high-level first); when they want low-level details, they read the code => never document low-level or trivial logic.
- Aim for 100% coverage of the *business logic* — not of the file tree. A file inventory with one-liners is a map, not a spec.
- DRY: every sentence earns its place — either it's a high-level summary of what the code implements, or it's business knowledge that isn't written in the code.
- ELI5: simple terms, no jargon, assume zero knowledge about the code — but full knowledge of the project's goals. That's the target reader: knows the project, hasn't read the code.

# Content

```md
One-sentence description of the business logic this file/directory implements.

## TLDR

- What happens, from a bird's view
- ...

## Flows

All high-level flows.

## Before modifying this file

Read this file's format at https://raw.githubusercontent.com/brillout/sdd/refs/heads/main/sdd.md
```

Notes:
- All `##` sections are optional — for a small file, the one-sentence description can be enough
- Consider using graphics (e.g. `mermaid` code blocks) whenever helpful

# What gets a SPEC.md

Only code carrying *major* business logic. Skip:
- Tests
- Demos and examples
- Assets (`.svg`, ...)
- Small/trivial utility files
- Repository machinery: build scripts, CI workflows, monorepo/tooling config
- ...

# Hierarchy

The file structure often represents levels of abstraction => mirror it:
- Root `SPEC.md` => the highest-level answer to "what does this software do, and how?" — the product's story, plus how the top-level subsystems relate. Not a repository overview.
- Deeper `SPEC.md` files => each subsystem's story.
