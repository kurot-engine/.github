# Support

Kurot is an open-source project maintained on a best-effort basis.

## Where to ask

- **Reproducible bug:** open a Bug Report in the affected repository.
- **Feature proposal:** open a Feature Request with a concrete use case.
- **Security vulnerability:** submit a private report through the repository's Security tab.
- **Usage question:** use GitHub Discussions when enabled, or provide a minimal example in an issue if the behavior appears to be an engine defect.

## Find the right project

- [Engine issues](https://github.com/kurot-engine/kurot/issues): Core, UI, Game,
  CLI, document/runtime contracts, fonts, atlases and DragonBones integration.
- [Spine adapter issues](https://github.com/kurot-engine/kurot-spine/issues):
  Spine integration, including the matching adapter and skeleton export version.
- [Editor issues](https://github.com/kurot-engine/kurot-editor-release/issues):
  desktop editing, project files, installation and updates.
- [Editor releases](https://github.com/kurot-engine/kurot-editor-release/releases):
  installers and release notes.

For API usage and compatibility, start with the
[engine package index](https://github.com/kurot-engine/kurot#packages-and-dependencies)
and the relevant package README. Current KUI projects and legacy EXML projects
use different CLI lines; include the authored file format in compilation reports.

## Include a reproduction

When requesting help, include the exact installed `@kurot/*` package versions, browser,
operating system, rendering backend when known, relevant logs, and a minimal
reproduction. Screenshots are useful for visual problems but should accompany
reproduction steps or code whenever possible.

For Editor reports, include the app version, operating system, steps and a
minimal sample Skin when relevant. For compilation reports, include the CLI
version, relevant `kurot.config.ts` settings, KUI input and the failing command.
Report installed versions rather than only the ranges in `package.json`.

There is currently no guaranteed response time or private commercial support
channel. Please do not send credentials, private assets, access tokens, or
other sensitive information in public reports.
