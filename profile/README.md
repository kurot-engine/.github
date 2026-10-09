# Kurot Engine

Kurot is a 2D game engine for the modern web, built in **TypeScript, ESM and
ES2022**. It combines the familiar Egret display-object and EUI development
model with modern rendering, explicit package contracts and KUI authoring tools.

[Engine & documentation](https://github.com/kurot-engine/kurot) ·
[Editor releases](https://github.com/kurot-engine/kurot-editor-release/releases) ·
[Spine adapters](https://github.com/kurot-engine/kurot-spine)

## Familiar APIs, modern foundations

- **Display objects and events:** a retained scene graph, transforms, graphics,
  input, textures, resources and media, with familiar `DisplayObject` APIs.
- **Rendering:** WebGL 2 preferred, WebGL 1 supported, multi-texture batching and
  a flat `InstructionSet` / `RenderPipe` execution path. Canvas 2D provides a
  separate fallback renderer.
- **UI:** EUI-style components, layouts, skins, states, data binding and themes,
  including independent plain, rich and bitmap text components.
- **Game systems:** Tween, MovieClip, scrolling, particles and skeletal animation
  through native DragonBones integration and separate versioned Spine adapters.
- **Authoring:** KUI XML, a desktop Skin editor, shared project styles and
  resources, and build-time ESM Skin compilation.

Kurot maintains its own resource formats, tooling and release contracts.
Consult the package documentation when adapting an Egret project.

## Engine packages

The [engine repository](https://github.com/kurot-engine/kurot) contains nine
independently versioned packages:

| Package | Responsibility |
| --- | --- |
| [`@kurot/core`](https://github.com/kurot-engine/kurot/tree/main/packages/core) | Display objects, rendering, events, geometry, text, resources, networking and media. |
| [`@kurot/ui`](https://github.com/kurot-engine/kurot/tree/main/packages/ui) | UI components, layout, skins, states, themes and data binding. |
| [`@kurot/game`](https://github.com/kurot-engine/kurot/tree/main/packages/game) | Tween, MovieClip, scrolling, particles and game helpers. |
| [`@kurot/cli`](https://github.com/kurot-engine/kurot/tree/main/packages/cli) | Project scaffolding, KUI Skin compilation, development serving and release builds. |
| [`@kurot/ui-document`](https://github.com/kurot-engine/kurot/tree/main/packages/ui-document) | Headless UI assets, component schemas, validation, transactions and undo/redo. |
| [`@kurot/ui-runtime`](https://github.com/kurot-engine/kurot/tree/main/packages/ui-runtime) | Browser materialization of semantic documents, reuse, appearances, bindings, actions and transitions. |
| [`@kurot/atlas`](https://github.com/kurot-engine/kurot/tree/main/packages/atlas) | Independent RGBA atlas packing, with a separate Node PNG adapter. |
| [`@kurot/dragonbones`](https://github.com/kurot-engine/kurot/tree/main/packages/dragonbones) | DragonBones runtime and native Kurot display, mesh, atlas, event and clock integration. |
| [`@kurot/bitmap-font`](https://github.com/kurot-engine/kurot/tree/main/packages/bitmap-font) | Headless bitmap-font parsing, validation, serialization and layout. |

Core uses the bitmap-font kernel. UI, Game and DragonBones use the application's
Core instance. CLI uses ui-document at build time; ui-runtime connects semantic
documents to native Core/UI objects. Atlas remains independent build-time tooling.

Current versions, compatibility requirements and release notes live in the
[engine README](https://github.com/kurot-engine/kurot#packages-and-dependencies)
and each package's documentation. See the
[dependency and release policy](https://github.com/kurot-engine/kurot/blob/main/docs/dependency-policy.md)
for targeted upgrades and independent releases.

## Design and build UI

[Kurot Editor](https://github.com/kurot-engine/kurot-editor-release) is the desktop
UI editor for Kurot projects. Its workflow covers Skin layouts, text, resources,
nine-slice grids, project styles and localization.

```text
Kurot Editor → project .kui.xml → Kurot CLI → ESM Skin factories → UI + Core
```

The editor saves canonical KUI XML into the project. CLI compiles those Skin
files and generates theme output and typed Skin parts; the game uses the
compiled modules through native UI. This path does not require ui-runtime or
XML parsing in the browser.

The semantic-document path is separate:

```text
ui-document → validated semantic assets → ui-runtime → native UI + Core
```

It supports programmatic assets, reusable instances, bindings, actions and
transitions. Canonical KUI XML authors Skin appearances; semantic screen and
reusable-component assets retain their programmatic boundary.

Current CLI 3.x targets KUI and the Editor workflow. Existing EXML game projects
retain the independent CLI 1.3.x line. See
[CLI documentation](https://github.com/kurot-engine/kurot/tree/main/packages/cli)
before changing an existing project's toolchain.

## Spine integration

[Kurot Spine](https://github.com/kurot-engine/kurot-spine) maintains separate
adapters for Spine 4.0, 4.1, 4.2 and 4.3. Choose the adapter matching the
skeleton's export/runtime line and check its Core peer requirement.

## How the project is maintained

Kurot is maintained by one developer working alongside AI assistance. Strict
types, named exports, focused modules and package `ai-context.md` maps help
keep the architecture understandable for contributors and future sessions.

Bug reports, focused fixes, documentation corrections and reproducible examples
are welcome. Read the
[contribution guide](https://github.com/kurot-engine/.github/blob/main/CONTRIBUTING.md)
and [support guide](https://github.com/kurot-engine/.github/blob/main/SUPPORT.md).
Report Editor issues in its
[public release repository](https://github.com/kurot-engine/kurot-editor-release/issues).
