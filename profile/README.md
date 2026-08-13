# Kurot Engine

Kurot is a web-focused 2D game engine — a modern rewrite of the Egret engine, rebuilt from the ground up in TypeScript.

## Why does this exist?

Egret powered a generation of H5 games, and its API shape — `DisplayObject`, events, graphics, EUI, EXML skins — is still a comfortable and productive way to build 2D games for the browser. But its internals carry the weight of an earlier era: prototype mixins, runtime XML parsing, global namespace reflection, JavaScript-first conventions that don't map cleanly onto strict types.

Kurot is an attempt to keep what was good about that developer experience and rebuild everything underneath for modern browsers — ESM, ES2022, strict TypeScript, an instruction-based render pipeline — so the same mental model runs on a foundation that isn't fighting its own history.

This isn't a drop-in replacement or a compatibility shim. It's a from-scratch engine that happens to share a familiar API surface, written to be readable, type-safe, and maintainable by a small number of people.

## How it's built

Kurot is, for now, a one-person project — built by a single developer working alongside AI assistance.

That's not a caveat; it's part of the point. The codebase is deliberately structured to make that sustainable: strict types, named exports, no `any`, files kept small, and an `ai-context.md` map in every package so that any session — human or AI — can get oriented without re-deriving the architecture from scratch. The goal is an engine that a small team (or one person and their tools) can actually understand and evolve, rather than a black box.

## Where to find it

The engine lives in a single monorepo:

- 📦 **[Kurot](https://github.com/kurot-engine/Kurot)** — the engine packages, CLI, examples, and architecture docs.

Each package there has its own README and documentation with the technical details. This page is just the front door.
