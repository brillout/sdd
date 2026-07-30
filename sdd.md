For each file and directory containing software source code, generate a `spec.md` file.
- `some-file.ext` => `some-file.spec.ext`
- `some-dir/` => `some-dir/spec.md`

Content:

```md
One-sentence description of what this file/directory does.

## TLDR

- Code does this
- And that
- ...

## Problems

List of non-obvious problems.

## Decisions

List of non-obvious decisions.

## Facts

List of non-obvious uncommon knowledge.

## Flows

List of all high-level flows.

## Before modifying this file

Read https://raw.githubusercontent.com/brillout/sdd/refs/heads/main/sdd.md
```

Notes:
- The goal `spec.md` is for humans to quickly get a high-level understanding of the business logic — keep it all high-level:
  - Humans reasons top-down (high-level first)
  - If a human wants low-level details, he can look at the code => no need to document low-level or trivial logic
- Aim for 100% *high-level* coverage, while keeping spec.md as succinct as possible
  - Only cover business logic that is both *major* (plays a central and crucial role) and *high-level* (don't describe what code does, describe the high-level idea the code implements)
- DRY
  - Every content should earn its place: either it's a high-level summary of knowledge written in code, or it's knowledge not written in code
- ELI5
  - Explain in simple terms, without jargon, assuming zero prior knowledge about the code
  - However, you *can* and *should* assume the reader is familiar with the *high-level* goals of the project — that's your target audience: zero knowledge about the code, but knowledge about the project
- All `##` sections are optional, e.g. small file => one-sentence description can be enough
- Don't create `spec.md` for code that doesn't represent business logic, and also skip minor business logic, for example:
  - Tests
  - `.svg`
  - Demo and examples
  - Small/trivial utility files
  - ...
