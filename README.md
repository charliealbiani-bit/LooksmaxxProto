# LooksmaxxProto
# Looksmaxxer Idle (Godot 4)

A beginner-friendly parody idle clicker inspired by Cookie Clicker-style loops.

## Folder Structure

```text
LooksmaxxerIdle/
├── project.godot
├── README.md
├── scenes/
│   └── Main.tscn
└── scripts/
    ├── Main.gd
    ├── managers/
    │   ├── CurrencyManager.gd
    │   ├── GameManager.gd
    │   ├── SaveManager.gd
    │   └── UpgradeManager.gd
    └── ui/
        └── UIManager.gd
```

## Scene Setup (already included)

`Main.tscn` contains:
- **TopBar**: Looks Points, stage, passive/s, click value.
- **Center click button**: main active income action.
- **Upgrade panel**: scrollable list of all upgrade buttons.
- **Passive timer**: ticks every 0.2 seconds for smooth passive gain.
- **Autosave timer**: writes JSON save every 15 seconds.

## Core Systems

- **CurrencyManager**: current points, click value, passive rate, add/spend logic.
- **UpgradeManager**: upgrade definitions (name/cost/level/bonuses/scaling), buying, recalc stats.
- **GameManager**: progression stage mapping.
- **SaveManager**: JSON save/load + offline earnings at 50% efficiency (8h cap).
- **UIManager**: builds shop buttons dynamically and refreshes labels.

## Beginner Notes on Balancing

- Cost formula: `base_cost * pow(1.15, level)`.
- Early upgrades are cheap and give small but frequent progress.
- Later upgrades heavily increase passive income for idle progression.

## Run in Godot 4

1. Install **Godot 4.2+**.
2. Open Godot → **Import** → select `LooksmaxxerIdle/project.godot`.
3. Press **F5** to run.
4. Click the main button, buy upgrades, and watch passive income grow.

## Export Setup (HTML5, Android, iOS, CrazyGames)

1. Open **Project > Export**.
2. Add presets:
   - Web (HTML5)
   - Android
   - iOS
3. In **Project Settings > Display**, keep stretch mode as `canvas_items` and aspect `expand` for responsive UI.
4. Keep save path as `user://looksmaxxer_save.json` (works cross-platform).
5. For CrazyGames/web:
   - Export Web preset.
   - Enable compression/gzip in hosting.
   - Keep assets lightweight (this project uses only built-in UI nodes and scripts).

## Mobile/Browser Performance Tips

- Lightweight UI only (no external textures).
- Passive updates run via a low-cost timer.
- Upgrade list is built once and refreshed on purchases.
- Autosave interval avoids frequent disk writes.
