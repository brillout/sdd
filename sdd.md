For each file and directory containing software source code, a `SPEC.md` file describes the high-level business logic.
- `some-file.ext` => `some-file.SPEC.md`
- `some-dir/` => `some-dir/SPEC.md`


## Goal

A `SPEC.md` is the answer a human gives when a colleague asks "how does this work?" — the high-level business logic, nothing else.

Litmus test: every sentence must be one you'd *say out loud* when explaining how it works. Sentences about the repository itself (build, CI, release, packaging, tooling) or about code itself (flags, clever tricks) fail the test — that's how the code works, not how the product works.

- Humans reason top-down (high-level first); when they want low-level details, they read the code => never document low-level or trivial logic.
- 100% coverage of *high-level* business logic, skip details
- Every sentence earns its place — zero low-level details, only high-level explanations
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
- Skip examples and demos
- For files that don't carry much business logic, consider creating a SPEC.md with only a one-sentence description.
- For tests, create a succinct SPEC.md describing what the tests cover


## Hierarchy

The file structure often represents levels of abstraction => mirror it:
- Root `SPEC.md` => the highest-level answer to "what does this software do, and how?" — the high-level product's story, plus how the top-level subsystems relate. Not a low-level repository overview.
- Deeper `SPEC.md` files => each subsystem's story.


## Install

1. Generate a `SPEC.md` file for each file and directory containing software source code
2. Make sure `AGENTS.md` mentions a sentence like this: "Before writing SPEC.md files, read https://raw.githubusercontent.com/brillout/sdd/refs/heads/main/sdd.md"
