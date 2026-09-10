# Contributing to grand-central

These workflows are depended on by other repos, so changes here get extra scrutiny. Please read this before opening a PR.

## 1. Small fix vs. new workflow

- **Small fix** (typo, bumping an action version inside an existing workflow): just open a PR.
- **New reusable workflow, or a breaking change to an existing one**: open a **Workflow Proposal** issue first so the design gets agreed on before code is written.

## 2. Writing a reusable workflow

- Every reusable workflow must use `on: workflow_call` and declare its `inputs` / `secrets` explicitly — no implicit assumptions about the caller's repo layout.
- Keep one workflow focused on one job (build-and-test, deploy, release) rather than one giant workflow with lots of conditionals.
- Document the workflow at the top of the file as a YAML comment: what it does, its inputs, and a `uses:` example.

## 3. Open your PR

Use the PR template checklist. At minimum:

- `actionlint` passes (runs automatically on your PR)
- You bumped the version note in [CHANGELOG.md](./CHANGELOG.md)
- If this changes an existing workflow's inputs/outputs, you called that out explicitly (it may be a breaking change)

## 4. Review and release

A CODEOWNER reviews for correctness and blast radius (who else calls this workflow). Once merged:

- Non-breaking changes get a new minor tag (e.g. `v1.3`) and the major tag (`v1`) is moved forward.
- Breaking changes get a new major tag (`v2`) and the old major tag (`v1`) is left alone so existing consumers don't break silently.

## Questions

Open a discussion, or comment on your proposal issue.
