# zed-portland

[Zed](https://zed.dev) language support for
[Portland](https://github.com/portlandlang/portland) (`.pdx`) — a joyous
programming language for Apple silicon.

## What it does (v0)

Registers the Portland language for `.pdx` files, borrowing the
[tree-sitter-ruby](https://github.com/tree-sitter/tree-sitter-ruby)
grammar — Portland keeps Ruby's surface, so Ruby highlighting is
almost-right today. Highlighting, brackets, indent rules (including
`struct`/`together`/`end`), outline, and `?`/`!` as word characters, with
no manual mode switching.

As the languages drift, the grammar forks into `tree-sitter-portland`
(Portland keywords in; removed Ruby syntax out) — tracked in
[portland#24](https://github.com/portlandlang/portland/issues/24).

## Install (dev)

1. Clone this repo.
2. In Zed: `zed: install dev extension` → pick this folder.
3. **Wait.** The first install downloads the ~70 MB wasi-sdk toolchain
   and compiles the grammar, silently, for a few minutes. Quitting Zed
   mid-build kills it *silently* — the extension never registers, and
   Zed won't resume on restart. If that happens: delete
   `~/Library/Application Support/Zed/extensions/build/wasi-sdk*` and
   reinstall. It's done when Portland appears in the Extensions panel
   (DEV badge). One-time cost; later rebuilds take seconds.
4. Open any `.pdx` file — the status bar should say Portland.

## Not yet

- A Portland-specific grammar (`~` task lines, `mutable`, `meanwhile`
  highlighted as keywords; `$globals` and friends un-highlighted)
- Language server anything
- Publication to the Zed extension registry
