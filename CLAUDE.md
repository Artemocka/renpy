# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Ren'Py visual novel game called "Ведьмин час" (The Witching Hour) — a Harry Potter fan fiction set at Hogwarts in the late 19th century, written in Russian.

## Running the Game

Open the project in the Ren'Py launcher and press "Launch Project", or run from the command line:

```bash
renpy .
```

There is no build/lint/test system — Ren'Py compiles `.rpy` files to `.rpyc` bytecode automatically on launch.

## Architecture

Ren'Py loads files in this order at startup:

1. **`options.rpy`** — Game config: title, version, resolution (1920×1080), audio settings, transitions, save directory
2. **`gui.rpy`** — UI styling: color palette (magenta `#cc0066` accent, dark purple `#510028` muted), fonts (DejaVuSans), dimensions
3. **`screens.rpy`** — All UI screens (~1620 lines): dialogue, menus, save/load, preferences, history, help, mobile variants
4. **`script.rpy`** — Game logic and story (currently a placeholder `label start`)

Additional directories:
- **`gui/`** — UI image assets; `gui/phone/` has mobile variants
- **`images/`** — Character sprites and backgrounds (currently empty)
- **`audio/`** — Music and sound effects (currently empty)
- **`tl/None/`** — Auto-generated translation/string files

## Story & Characters

The plot is documented in **`сюжет.MD`** (Russian). Five main characters:
- **Эвелина Нотар** (Slytherin) — ambitious, politician's daughter
- **Теодор Роули** (Slytherin) — intellectual cynic
- **Корнелиус Вейн** (Ravenclaw) — rune/dark magic specialist
- **Мэри Олбрайт** (Ravenclaw) — shy seer
- **Себастьян Морвуд** (Slytherin) — cursed family heir

The story centers on "The Midnight Hour Chronicle" — a forbidden book tied to an ancient resurrection ritual, with 5 main endings + 1 secret ending.

## Key Implementation Notes

- All dialogue and UI text is in **Russian**
- Character definition example: `define e = Character('Имя', color="#xxxxxx")`
- Story labels go in `script.rpy` as `label scene_name:` blocks
- New screens belong in `screens.rpy`; follow existing patterns (use `screen`, `use`, `vbox`, `hbox`, `textbutton`)
- `.rpyc` and `cache/` files are auto-generated — do not edit them
- VS Code is configured to hide compiled files from the explorer (`.vscode/settings.json`)
