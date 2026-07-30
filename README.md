# Spec-driven development

#### Get started

Tell AI:

```
Apply https://raw.githubusercontent.com/brillout/sdd/refs/heads/main/sdd.md
```

[https://raw.githubusercontent.com/brillout/sdd/refs/heads/main/sdd.md](https://raw.githubusercontent.com/brillout/sdd/refs/heads/main/sdd.md) is just the raw link of the `ssd.md` file of this repository.

#### What does it do?

- AI generates `.spec.md` for each source code file:
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
  ```
- AI will maintain these `.spec.md` files

#### Why?

It enables you to:
- When AI makes a change, quickly read the modified business logic instead of reading code
- Quickly navigate unfamiliar code

#### How does it work?

To understand how it works, read the `sdd.md` file — it's small.
