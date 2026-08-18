# .github

Organization-wide defaults for Heim-Lab repositories.

GitHub uses the community health files in this repository for any organization repository that does not define its own copy. This repository must stay **public** for those defaults to apply.

## What is inherited

| File | Purpose |
|------|---------|
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | Commit convention, pull request rules, and merge policy |
| [`.github/pull_request_template.md`](.github/pull_request_template.md) | Form shown when opening a pull request |

A repository can override any of these by adding a file at the same path.

These files are **not** inherited from this repository: `CODEOWNERS`, licenses, `.gitignore`, and GitHub Actions workflows. Put those in each project, or call reusable workflows explicitly.

## Conventions

All projects follow [`CONTRIBUTING.md`](CONTRIBUTING.md):

- Conventional Commits on the default branch
- Changes land through pull requests
- Pull requests are squash-merged; the PR title becomes the commit on `main`

## Local overrides

GitHub looks for a file in the project first, then falls back to this repository:

1. `.github/` in the project
2. repository root
3. `docs/`
4. this `.github` repository, in the same order

If a project adds any file under its own `.github/ISSUE_TEMPLATE/`, organization issue templates are ignored for that project. The same idea applies to a local pull request template: it replaces the org default entirely.
