For each file and directory containing software source code, a `SPEC.md` file describes what the code does.
- `some-file.ext` => `some-file.SPEC.md`
- `some-dir/` => `some-dir/SPEC.md`


## Goal

AI writes the code; the engineer stays in control of the business logic. `SPEC.md` files are where that control happens: reviewing a change means reading its spec diff, and understanding any part of the system means reading its spec — never the code.

A `SPEC.md` is the answer to "how does this work?" — the business logic, nothing else.

Write for exactly one reader: a technical product manager — knows the project and its user stories, proficient in programming and software engineering, never reads the code. Two consequences:
- Assume zero knowledge about the code. Technical writing is fine; presupposing what the code looks like is not.
- Write prose meant to be read, not transcribed speech: the reader cannot see the screen, cannot watch you point, and cannot ask a follow-up question. Every sentence must survive that reader.

What belongs in a spec:
- 100% of the high-level business logic, from a bird's view — no implementation details.
- Everything the user can see or do. A tooltip, a truncated label, a disabled button: that's business logic, never an implementation detail.
- The user-story perspective throughout — `## Flows` describes how the user stories are fulfilled.
- Litmus test: a sentence belongs if you'd say it out loud when explaining how the product works. Sentences about the repository (build, CI, release, packaging, tooling) or about the code itself (flags, clever tricks) fail the test — they explain how the code works, not how the product works.
- A direct mapping between explanation and code — the only place for additional context is `## Rationales`.

How a spec is written:
- Zero ambiguity: the reader must never second-guess what a sentence means.
- Name referents, never gesture at them:
  - Files and components => their real code name (`TopNav`), never an invented stand-in ("the page's header"). The real name is greppable and leads the reader to that component's own `SPEC.md`.
  - UI mechanisms => their standard name: "in a tooltip on hover", not "behind a hover".
  - Pronouns => antecedent in the same sentence, or repeat the noun.
- One concept => one name, used verbatim across all `SPEC.md` files. Never rotate synonyms (the same thing called *session* here and *run* there): the reader must assume different words mean different things.
- No new jargon. When unavoidable, explain it in `## Glossary`.
- Short by omission, not by compression: drop a detail rather than pack three facts into one dense clause-chain.
- Minimal prior reading: each sentence understandable on its own.


## File content

```md
One-sentence description of the business logic this file/directory implements.

## User Stories

List of user stories that the flows below support.

## Flows — TL;DR

List of one-sentence succinct summary of the flows below.

## Flows

List of all high-level business logic and how they fulfill user stories.

## Rationales

List of non-straightforward rationales for the flows above.

## Glossary

List of jargon explanations.

## Before modifying/creating SPEC.md files

You must always read and respect https://raw.githubusercontent.com/brillout/sdd/refs/heads/main/sdd.md
```

Notes:
- Sections:
  - `## Before modifying/creating SPEC.md files` must never be omitted
  - The other `##` sections are optional (e.g. for a small file, the one-sentence description can be enough)
  - Never create other `##` sections not listed above
- For each flow, always consider using a `mermaid` graphic
- Skip usage examples and demos
  - Exception: for a visual component, a one-line example rendering (e.g. `⚠ 3 errors · <latest error headline>`) is specification, not demo — one such line often replaces sentences of layout prose
- For tests, create a succinct `SPEC.md` describing what the tests cover


## Hierarchy

The file structure often represents levels of abstraction => mirror it:
- Root `SPEC.md`:
  - The highest-level answer to "what does this software do?" — the high-level product's story
  - How the top-level subsystems relate (instead of a low-level repository overview)
- Deeper `SPEC.md` files => each subsystem's story
- Shared vocabulary lives up the tree: a term used by several specs is defined once, in the `## Glossary` of the closest `SPEC.md` above all of them, and reused verbatim below


## Install

1. Generate a `SPEC.md` file for each file and directory containing software source code
2. Make sure `AGENTS.md` contains: "Before modifying/creating SPEC.md files, you must always read and respect https://raw.githubusercontent.com/brillout/sdd/refs/heads/main/sdd.md"
