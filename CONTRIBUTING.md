# Contributing to Kurot

Thank you for helping improve Kurot. Bug reports, focused fixes,
documentation corrections, tests, and carefully scoped features are welcome.

## Before opening an issue

- Search existing issues and discussions for the same problem.
- Record exact installed package or application versions and, when practical,
  reproduce the problem with the latest compatible published versions.
- Reduce bugs to the smallest reproducible example you can provide.
- Use a security advisory instead of a public issue for vulnerabilities.

Questions about using the engine belong in GitHub Discussions when that
feature is available. Reproducible engine defects belong in Issues.

## Choose the repository

- [Kurot](https://github.com/kurot-engine/kurot): engine packages, KUI compilation,
  shared UI contracts, examples and engine documentation.
- [Kurot Spine](https://github.com/kurot-engine/kurot-spine): versioned Spine
  adapters and their examples. Include the Spine export/runtime line in reports.
- [Kurot Editor releases](https://github.com/kurot-engine/kurot-editor-release):
  desktop Editor bugs, feature requests, installation and update feedback.
  This is the public release and feedback repository.
- [Organization documentation](https://github.com/kurot-engine/.github): this
  shared guide, issue templates and the organization profile.

## Development setup

Kurot packages are strict TypeScript and ESM projects. Use Node.js 20 or later
and the pnpm version declared by the package you are changing.

The engine repository has no root pnpm workspace or unified install/build/test
command. Each SDK package has its own manifest, installation and lockfile.
For example, from the engine repository root:

```sh
pnpm --dir packages/core install
pnpm --dir packages/core build
pnpm --dir packages/core test
git diff --check
```

All nine engine packages and the current Spine adapters provide build and test
scripts. Read the affected package's README for additional type checks, packed
compatibility checks, examples and browser verification. Rendering and UI fixes
should include a reproduction checked in the affected backend when applicable.

Application repositories follow their own documented runtime, package manager
and release workflow. Documentation-only changes need content/link checks and
`git diff --check`; they do not require rebuilding unchanged SDKs.

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

## Dependencies and releases

Follow the affected repository's policy. For engine packages, read the
[dependency and release policy](https://github.com/kurot-engine/kurot/blob/main/docs/dependency-policy.md).

- Package versions are independent. A compatible dependency patch does not
  require new releases of unchanged SDKs.
- Core/UI peers express the minimum required host API or contract. Development
  dependencies and lockfiles record the tested checkout; a newer development
  baseline does not automatically raise a peer minimum.
- Core's bitmap-font kernel and CLI's ui-document kernel are ordinary
  dependencies. UI, Game, DragonBones and ui-runtime declare their host contracts
  through peers. Keep one compatible Core instance when exchanging native objects.
- Classify consumer changes as required compatibility adoption, optional
  installation/lockfile adoption or unaffected. Update only the relevant packages
  and applications; avoid blanket `--latest` upgrades.
- A development-only declaration or lockfile update needs no SDK publication
  unless it changes generated or bundled shipped output. Applications adopt
  dependency fixes through their own installation, rebuild and release rules.
- A matching semantic format version does not prove compatible package APIs.
  Headless packages before 1.0 require particular care with 0.x minor ranges.
- When preparing a release, update the package version, dated CHANGELOG, README
  and affected context/dependency documentation. Build and test the changed
  package, then run relevant consumer checks for changed contracts.
- Verify publication in the registry before describing a version as published.
  Source versions and local builds alone do not establish publication.

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
