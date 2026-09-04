# Pigs in Space for Codex

Pigs in Space themes for Codex CLI and the Codex app. The CLI theme is ported
from the canonical
[Pigs in Space Zed theme](https://github.com/kreek/pigs-in-space-zed/blob/main/themes/pigs-in-space.json).

## Codex CLI

Codex CLI custom themes use the TextMate `.tmTheme` format. Install the theme:

```sh
mkdir -p "${CODEX_HOME:-$HOME/.codex}/themes"
cp pigs-in-space.tmTheme "${CODEX_HOME:-$HOME/.codex}/themes/pigs-in-space.tmTheme"
```

Then run `/theme` in Codex and select `pigs-in-space`. Alternatively, add this
to `${CODEX_HOME:-$HOME/.codex}/config.toml`:

```toml
[tui]
theme = "pigs-in-space"
```

The CLI theme controls fenced-code syntax foregrounds, added/deleted diff
colors, and theme-aware status-line accents. Codex currently renders foreground
colors and bold text, but not the theme's italic or underline styles. General
theme backgrounds, caret, selection, and line-highlight values do not recolor
the terminal UI; the surrounding interface continues to use the terminal's own
color palette. Diff backgrounds appear in truecolor terminals, are quantized in
ANSI-256 terminals, and are omitted in ANSI-16 terminals.

## Accessibility

The syntax foregrounds meet WCAG's 4.5:1 contrast guideline against the
canonical `#21262C` editor background and the theme's truecolor inserted and
deleted diff backgrounds. The comment color, `#7E9084`, is deliberately set
just above that threshold to remain as muted as possible.

Codex applies the terminal `DIM` attribute to syntax on deleted diff lines
after the theme is rendered. The resulting contrast varies by terminal and
cannot be controlled by a TextMate theme, so deleted-line text may fall below
4.5:1 in terminals that substantially dim foreground colors.

Canonical Zed palette mappings used by the CLI theme include:

- `background`: `#21262C`
- `editor.foreground`: `#A0B0C1`
- `text.accent`: `#4C9C9D`
- `created`: `#C3E88D`
- `deleted`: `#FF5370`
- `syntax.keyword`: `#AC8497`

The `.tmTheme` uses dark green and red diff backgrounds rather than Zed's
translucent overlays because Codex reads diff backgrounds as opaque RGB colors.

## Codex app

The existing, separate Codex app theme artifact is preserved in this directory.
Its current import string is:

```text
codex-theme-v1:{"codeThemeId":"dracula","theme":{"accent":"#ff79c6","contrast":60,"fonts":{"code":"Bitstream Vera Sans Mono","ui":null},"ink":"#f8f8f2","opaqueWindows":true,"semanticColors":{"diffAdded":"#50fa7b","diffRemoved":"#ff5555","skill":"#ff79c6"},"surface":"#282a36"},"variant":"dark"}
```

Codex app themes use a different `codex-theme-v1` format and are not loaded by
Codex CLI.
