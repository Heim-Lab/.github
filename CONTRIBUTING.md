# Development Guidelines

This document defines the development conventions used across all projects.

## Commit Convention

The commit that lands on the default branch must follow the Conventional Commits specification. Repositories squash-merge pull requests, so that commit is the pull request title.

```text
<type>(<scope>): <description>
```

The scope is optional.

Examples:

| Without scope                                 | With scope                                |
|-----------------------------------------------|-------------------------------------------|
| feat: add account synchronization             | feat(api): add accounts endpoint          |
| fix: handle connection timeout                | fix(imap): handle server disconnect       |
| refactor: simplify repository implementation  | refactor(db): simplify contact repository |
| chore: update dependencies                    | build(docker): update Python image        |


## Commit Types

| Type       | Description                                                       | Example                                            |
|------------|-------------------------------------------------------------------|----------------------------------------------------|
| `feat`     | A new feature or functionality.                                   | `feat(api): add contact search`                    |
| `fix`      | A bug fix.                                                        | `fix(sync): handle connection timeout`             |
| `refactor` | Code changes that neither fix a bug nor add a feature.            | `refactor(api): extract account service`           |
| `perf`     | Performance improvements.                                         | `perf(parser): reduce message parsing allocations` |
| `test`     | Adding or modifying tests.                                        | `test(api): add account endpoint tests`            |
| `docs`     | Documentation-only changes.                                       | `docs: update installation instructions`           |
| `build`    | Changes related to the build system, dependencies, or containers. | `build(docker): update Python base image`          |
| `ci`       | Changes to CI/CD configuration.                                   | `ci: add mypy checks`                              |
| `chore`    | Maintenance tasks that do not modify application behavior.        | `chore(deps): update dependencies`                 |
| `style`    | Formatting or code-style changes that do not affect behavior.     | `style: apply code formatting`                     |
| `revert`   | Reverts a previous commit.                                        | `revert: revert account synchronization changes`   |


## Pull Requests

All changes reach the default branch through a pull request. Do not push to `main` directly.

Pull requests are squash-merged. Intermediate commits on the branch do not appear on `main`; the pull request title becomes the commit message. Feature-branch commits may be informal.

Complete the pull request checklist before requesting review.

### Scope

Each pull request should contain one logical change. Split unrelated fixes, refactors, and dependency updates into separate PRs.

### Title

The title must follow the Conventional Commits format described above:

```text
<type>(<scope>): <description>
```

This title is the commit that remains on `main` after squash-merge.

### Description

The description must include:

- why the change is needed
- what changed
- how it was verified

Link related issues with `Closes #123` when applicable.

### Self-review

Review your own diff before requesting review. Remove debug leftovers, stray files, and unrelated edits.

### Style

Follow the formatter, linter, and style tools of that repository. If the repository has no style tooling, match the surrounding code. Do not mix unrelated formatting with behavior changes.

### Tests

If the repository has a test suite, include tests for behavior changes. If it does not, this requirement does not apply.

### Secrets

Do not include secrets, credentials, or local environment files.

### Review and merge

- Open the pull request as a draft until it is ready for review.
- CI must be green before merge.
- At least one approving review is required, except in repositories with a single maintainer.
- Update the branch from the default branch and resolve conflicts before the final review.
- Squash-merge using the pull request title as the commit message. Do not use merge commits.
- Delete the branch after merge.




Pull Requests - Allow merge commits Loading
When merging pull requests, you can allow any combination of merge commits, squashing, or rebasing. At least one option must be enabled. If you have linear history requirement enabled on any protected branch, you must enable squashing or rebasing.



