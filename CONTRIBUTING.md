# Contributing to Kurot

Thank you for helping improve Kurot. Bug reports, focused fixes,
documentation corrections, tests, and carefully scoped features are welcome.

## Before opening an issue

- Search existing issues and discussions for the same problem.
- Confirm the problem with the latest published package versions.
- Reduce bugs to the smallest reproducible example you can provide.
- Use a security advisory instead of a public issue for vulnerabilities.

Questions about using the engine belong in GitHub Discussions when that
feature is available. Reproducible engine defects belong in Issues.

## Development setup

Kurot packages are strict TypeScript and ESM projects. Use Node.js 20 or later
and the pnpm version declared by the package you are changing.

Install, build, and test from the affected package directory:

```sh
pnpm install
pnpm build
pnpm test
```

Some adapter packages do not yet provide automated tests. In that case, build
the package and run its example in a browser.

## Code expectations

- Preserve strict TypeScript checks; do not introduce `any` or suppression comments.
- Use ESM and named exports.
- Declare return types on exported functions.
- Keep changes focused and avoid unrelated formatting or refactors.
- Add or update tests for behavior changes whenever a suitable test harness exists.
- Update public documentation when APIs, compatibility, or commands change.
- Do not add compatibility shims unless the project explicitly intends to support the old behavior.

Package-specific architecture and code rules take precedence over this shared
guide. Read the repository's `AGENTS.md`, package README, and `docs/` before
making structural changes.

## Pull requests

A pull request should explain:

- what problem it solves;
- why the chosen implementation is appropriate;
- which packages and public APIs are affected;
- how the change was tested;
- whether it changes rendering, assets, compatibility, or generated output.

Keep commits understandable and use a conventional prefix where practical,
for example `fix(core):`, `feat(ui):`, `refactor(cli):`, or `docs:`.

By contributing, you agree that your contribution is provided under the
license of the repository receiving it.
