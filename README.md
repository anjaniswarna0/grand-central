# grand-central

Reusable GitHub Actions **workflows** — the shared build/test/deploy recipes other repos call into with `uses:`, instead of copy-pasting the same YAML everywhere.

```yaml
jobs:
  build:
    uses: anjaniswarna0/grand-central/.github/workflows/reusable-build-and-test.yml@v1
    with:
      node-version: "20"
```

See [CONTRIBUTING.md](./CONTRIBUTING.md) to propose a change or add a new reusable workflow.

## How a change gets in

```
Contributor
   |
   v
(For bigger changes) opens a
"Workflow Proposal" issue
   |
   v
Design agreed in discussion
   |
   v
Branch created off grand-central
   |
   v
New/edited file added in
.github/workflows/*.yml
(must declare on: workflow_call)
   |
   v
Pull Request opened using
the PR template
   |
   v
Automated checks run
(actionlint, dry-run test workflow)
   |
   +-- Fails --> back to contributor
   |
   v (Passes)
Review by CODEOWNERS
   |
   v
Merge to main
   |
   v
Tag a new release (v2, v2.1, ...)
   |
   v
Consumers bump their @version
```
