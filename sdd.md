Describe the codebase's business logic in `SPEC.md` files, placed beside the code that implements it:
- `some-dir/` => `some-dir/SPEC.md`
- `some-file.ext` => `some-file.SPEC.md`


## Goal

A `SPEC.md` is the answer a human gives when a colleague asks "how does this work?" — the high-level business logic, nothing else.

Litmus test: every sentence must be one you'd *say out loud* when explaining how it works. Sentences about the repository itself (build, CI, release, packaging, tooling) or about code itself (flags, clever tricks) fail the test — that's how the code works, not how the product works.

- Humans reason top-down (high-level first); when they want low-level details, they read the code => never document low-level or trivial logic.
- Aim for 100% coverage of the *business logic* — not of the file tree. A file inventory with one-liners is a map, not a spec.
- Every sentence earns its place — zero low-level details, only high-level explanation
- ELI5: simple terms, no jargon, assume zero knowledge about the code — but full knowledge of the project's goals. That's the target reader: knows the project, hasn't read the code.


## File content

```md
One-sentence description of the business logic this file/directory implements.

## TLDR

List of one-sentence succinct summary of the content below.

## Flows

List of all flows, only high-level from a bird's view.

## Rationales

List of non-straightforward rationales for the flows above.

## Before writing SPEC.md files

Read https://raw.githubusercontent.com/brillout/sdd/refs/heads/main/sdd.md
```

Notes:
- Sections:
  - `## Before writing SPEC.md files` must never be omitted
  - The other `##` sections are optional (e.g. for a small file, the one-sentence description can be enough)
  - Don't create other `##` sections not listed above
- Consider using graphics (e.g. `mermaid` code blocks) whenever helpful


## What gets a SPEC.md

Only code carrying *major* business logic. Skip:
- Demos and examples
- Assets (`.svg`, ...)
- ...


## Hierarchy

The file structure often represents levels of abstraction => mirror it:
- Root `SPEC.md` => the highest-level answer to "what does this software do, and how?" — the product's story, plus how the top-level subsystems relate. Not a repository overview.
- Deeper `SPEC.md` files => each subsystem's story.


## Install

1. If the repository hasn't any `SPEC.md` yet, generate a `SPEC.md` file for each file and directory containing software source code
2. Make sure `AGENTS.md` mentions a sentence like: "Before writing SPEC.md files, read https://raw.githubusercontent.com/brillout/sdd/refs/heads/main/sdd.md"
