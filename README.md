# New Memo Labs project

> **Before creating a repository:** search both GitHub owners and the local project register for an existing canonical source; do not create mirror repositories. See the [GitHub ownership policy](https://github.com/memolabs-dev/.github/blob/main/docs/repository-ownership-policy.md). Confirm repository visibility explicitly; private work must remain private.\n\nCreated by Memo Bridge `project_create` from the template `memolabs-dev/project-template`.
Replace this paragraph with what the project is for.

- Tests: `npm test` (Node 22 or later, no dependency).
- CI: one check, `check`. Mergify merges green pull requests that touch no gate path
  (see `AGENTS.md`).

## Local pre-commit

Run `npm install` once after cloning (the `prepare` script installs the hook), or run
`npm run hooks:install` explicitly. The installer activates `core.hooksPath=.githooks`
and makes `.githooks/pre-commit` executable; it will not overwrite an existing custom
hooks path. Re-run after cloning a new worktree if it needs its own local config.

Each commit checks staged whitespace errors, rejects obvious private environment/key
files, and runs `npm run check:staged` (lightweight smoke tests by default). Adapt
`check:staged` to the project's stack; keep heavy integration/E2E tests in CI.
For an exceptional deliberate bypass use `git -c core.hooksPath=/dev/null commit`
(or `git commit --no-verify`); CI requirements still apply.
