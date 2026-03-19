# Keyboard Layout Backup — Sofle Choc 59-Key

> **Backup created**: 2026-03-18
> **Source**: `NiklasKranjc/zmk-sofle59key`
> **Upstream**: `KeyboardHoarders/zmk-sofle59key`
> **Hardware**: Sofle Choc 1 Encoder, nice!nano v2, nice!view display

This document backs up the complete custom keyboard layout configuration.
The authoritative files are `config/sofle.keymap` and `config/sofle.conf`.

---

## Dateien zum Sichern (Files to Back Up)

Um deine Keymap lokal zu sichern, lade diese Dateien herunter (z. B. über
**Code → Download ZIP** auf GitHub, oder klicke einzelne Dateien an und wähle
**Raw → Rechtsklick → Speichern unter**).

### Wichtigste Dateien (deine persönliche Konfiguration)

| Datei | Beschreibung |
|---|---|
| [`config/sofle.keymap`](config/sofle.keymap) | **Haupt-Keymap** — Layer, Combos, Makros, Behaviors |
| [`config/sofle.conf`](config/sofle.conf) | **Firmware-Einstellungen** — Bluetooth, Sleep, Encoder, Name |

### Build-Konfiguration (zum Kompilieren der Firmware)

| Datei | Beschreibung |
|---|---|
| [`build.yaml`](build.yaml) | GitHub-Actions-Build-Matrix (Board-/Shield-Kombinationen) |
| [`config/west.yml`](config/west.yml) | ZMK-Dependency-Manifest (Zephyr/West) |

### Visualisierung (optional)

| Datei | Beschreibung |
|---|---|
| [`keymap_drawer.config.yaml`](keymap_drawer.config.yaml) | Keymap-Drawer-Anzeigeeinstellungen |
| [`keymap-drawer/sofle.yaml`](keymap-drawer/sofle.yaml) | Geparste Keymap für die SVG-Generierung |
| [`keymap-drawer/sofle.svg`](keymap-drawer/sofle.svg) | Generiertes SVG-Bild deiner Keymap |

> **Tipp:** Am einfachsten ist es, das gesamte Repository als ZIP herunterzuladen:
> Gehe auf die [Repo-Hauptseite](https://github.com/NiklasKranjc/zmk-sofle59key),
> klicke auf den grünen **Code**-Button und dann auf **Download ZIP**.

---

## Layers Overview

| # | Name           | Purpose                                    |
|---|----------------|--------------------------------------------|
| 0 | `BASE`         | QWERTY with custom mod layout              |
| 1 | `LOWER`        | Numbers, symbols, F-keys, mouse buttons    |
| 2 | `RAISE`        | Navigation, clipboard, function keys       |
| 3 | `ADJUST`       | Bluetooth, ext power, ZMK Studio (LOWER+RAISE) |
| 4 | `EXTRA`        | Mouse movement and scrolling               |
| 5 | `ANSI_training`| Standard ANSI layout for practice          |
| 6 | `MausUndCAD`   | CAD-optimized layout with mouse right-hand |
| 7 | `CADnachMaus`  | CAD numpad overlay (on top of layer 6)     |

---

## Combos (8)

| Name           | Keys       | Action              |
|----------------|------------|----------------------|
| backspace      | 32 + 31    | `BSPC`              |
| delete         | 27 + 33    | `DELETE`             |
| esc            | 25 + 41    | `ESCAPE`             |
| ö              | 22 + 21    | `RA(P)` (AltGr+P)   |
| ü              | 19 + 20    | `RA(Y)` (AltGr+Y)   |
| ä              | 25 + 26    | `RA(Q)` (AltGr+Q)   |
| ß              | 26 + 27    | `RA(S)` (AltGr+S)   |
| stickyLeftALT  | 24 + 35    | Sticky `LEFT_ALT`    |

---

## Macros (4)

| Name                    | Action                              |
|-------------------------|--------------------------------------|
| `anfuerhrungszeichen`   | Double-quote + space (`LS(SQT) SPACE`) |
| `sticky_ss`             | Sticky Super+Shift                   |
| `sticky_ssa`            | Sticky Super+Alt+Shift               |
| `EuroAnsiInt`           | Euro sign `€` (`LA(LC(N4))`)         |

---

## Custom Behaviors

| Name  | Type            | Details                                     |
|-------|-----------------|---------------------------------------------|
| `skq` | Sticky key      | Quick-release, 3000 ms timeout, ignore mods |

---

## Encoder Configuration

- Triggers per rotation: **30**
- Left encoder steps: **60**
- Right encoder steps: **60**
- Default layer: Volume up/down
- Lower layer: Volume up/down
- Raise layer: Left/Right arrows
- Adjust/Extra layers: Volume up/down + PgUp/PgDn

---

## Layer 0 — BASE (default)

```
┌───────┬─────┬─────┬─────┬─────┬─────┐               ┌─────┬─────┬─────┬─────┬─────┬───────┐
│  ESC  │  1  │  2  │  3  │  4  │  5  │               │  6  │  7  │  8  │  9  │  0  │   -   │
├───────┼─────┼─────┼─────┼─────┼─────┤               ├─────┼─────┼─────┼─────┼─────┼───────┤
│  TAB  │  Q  │  W  │  E  │  R  │  T  │               │  Y  │  U  │  I  │  O  │  P  │ BSPC  │
├───────┼─────┼─────┼─────┼─────┼─────┤               ├─────┼─────┼─────┼─────┼─────┼───────┤
│ LCTRL │  A  │  S  │  D  │  F  │  G  │               │  H  │  J  │  K  │  L  │  ;  │  " ␣  │
├───────┼─────┼─────┼─────┼─────┼─────┼──────┐ ┌──────┼─────┼─────┼─────┼─────┼─────┼───────┤
│ LSHFT │  Z  │  X  │  C  │  V  │  B  │ MUTE │ │ MB1  │  N  │  M  │  ,  │  .  │  /  │ RSHFT │
└───────┴─────┼─────┼─────┼─────┼─────┼──────┤ ├──────┼─────┼─────┼─────┼─────┼─────┴───────┘
              │C+GUI│S+GUI│ GUI │LOWER│SPACE │ │ENTER │RAISE│ GUI │S+GUI│A+GUI│
              └─────┴─────┴─────┴─────┴──────┘ └──────┴─────┴─────┴─────┴─────┘
```

**Key customizations vs upstream:**
- `ESC` instead of `gresc` (grave-escape)
- `LCTRL` on left home row instead of `LSHFT`
- `LSHFT` on left bottom row instead of `LCTRL`
- `anfuerhrungszeichen` macro on right home pinky (double-quote + space)
- `C_MUTE` encoder button (left) + `MB1` mouse click (right)
- Thumb cluster: `Ctrl+GUI`, `Shift+GUI`, `GUI`, `LOWER`, `SPACE` | `ENTER`, `RAISE`, `GUI`, `Shift+GUI`, `Alt+GUI`

---

## Layer 1 — LOWER

```
┌───────┬─────┬─────┬─────┬─────┬─────┐               ┌─────┬──────┬──────┬──────┬──────┬───────┐
│ trans │ F1  │ F2  │ F3  │ F4  │ F5  │               │ F6  │  F7  │  F8  │  F9  │ F10  │  F11  │
├───────┼─────┼─────┼─────┼─────┼─────┤               ├─────┼──────┼──────┼──────┼──────┼───────┤
│ trans │  1  │  2  │  3  │  4  │  5  │               │  6  │   7  │   8  │   9  │   0  │  F12  │
├───────┼─────┼─────┼─────┼─────┼─────┤               ├─────┼──────┼──────┼──────┼──────┼───────┤
│sk LALT│  !  │  @  │  #  │  $  │  %  │               │  ^  │   &  │   *  │   (  │   )  │   '   │
├───────┼─────┼─────┼─────┼─────┼─────┼──────┐ ┌──────┼─────┼──────┼──────┼──────┼──────┼───────┤
│ trans │trans│ MB1 │ MB3 │ MB2 │  €  │trans │ │trans │trans│   -  │   =  │   [  │   ]  │   |   │
└───────┴─────┼─────┼─────┼─────┼─────┼──────┤ ├──────┼─────┼──────┼──────┼──────┼──────┴───────┘
              │trans│trans│trans│trans│trans │ │trans │trans│trans │trans │trans │
              └─────┴─────┴─────┴─────┴──────┘ └──────┴─────┴──────┴──────┴──────┘
```

---

## Layer 2 — RAISE

```
┌───────┬──────┬──────┬──────┬───────┬──────┐               ┌──────┬──────┬──────┬─────────┬─────┬──────┐
│ trans │trans │trans │trans │ trans │trans │               │trans │trans │trans │  trans  │trans│trans │
├───────┼──────┼──────┼──────┼───────┼──────┤               ├──────┼──────┼──────┼─────────┼─────┼──────┤
│ trans │ INS  │PSCRN │CMENU │ trans │trans │               │PG_UP │trans │  ↑   │  trans  │  0  │trans │
├───────┼──────┼──────┼──────┼───────┼──────┤               ├──────┼──────┼──────┼─────────┼─────┼──────┤
│ trans │ LALT │LCTRL │LSHFT │ trans │CAPS  │               │PG_DN │  ←   │  ↓   │    →    │ DEL │BSPC  │
├───────┼──────┼──────┼──────┼───────┼──────┼──────┐ ┌──────┼──────┼──────┼──────┼─────────┼─────┼──────┤
│ trans │UNDO  │ CUT  │COPY  │ PASTE │trans │PASTE │ │tog 6 │trans │tog 6 │SS    │SSA      │trans│trans │
└───────┴──────┼──────┼──────┼───────┼──────┼──────┤ ├──────┼──────┼──────┼──────┼─────────┼─────┴──────┘
               │trans │trans │ trans │trans │trans │ │trans │trans │trans │trans │  trans  │
               └──────┴──────┴───────┴──────┴──────┘ └──────┴──────┴──────┴──────┴─────────┘
```

**Custom:** `tog 6` toggles CAD layer, `sticky_ss` and `sticky_ssa` macros on right bottom row.

---

## Layer 3 — ADJUST (LOWER + RAISE)

```
┌──────────┬──────┬──────┬──────┬──────┬──────────┐               ┌─────┬─────┬─────┬─────┬─────┬─────┐
│BT_CLR_ALL│ BT 0 │ BT 1 │ BT 2 │ BT 3 │  BT 4   │               │none │none │none │none │none │none │
├──────────┼──────┼──────┼──────┼──────┼──────────┤               ├─────┼─────┼─────┼─────┼─────┼─────┤
│EP_TOG    │none  │none  │none  │none  │Studio Unl│               │none │none │none │none │none │none │
├──────────┼──────┼──────┼──────┼──────┼──────────┤               ├─────┼─────┼─────┼─────┼─────┼─────┤
│none      │none  │none  │none  │none  │none      │               │none │none │none │none │none │none │
├──────────┼──────┼──────┼──────┼──────┼──────────┼──────┐ ┌──────┼─────┼─────┼─────┼─────┼─────┼─────┤
│none      │none  │none  │none  │none  │Caps Word │ none │ │tog 5 │none │none │none │none │none │none │
└──────────┴──────┼──────┼──────┼──────┼──────────┼──────┤ ├──────┼─────┼─────┼─────┼─────┼─────┴─────┘
                  │none  │none  │none  │none      │ none │ │ none │none │none │none │none │
                  └──────┴──────┴──────┴──────────┴──────┘ └──────┴─────┴─────┴─────┴─────┘
```

---

## Layer 4 — EXTRA (mouse)

Mouse movement (WASD-style) and scroll on left hand, everything else `none`.

---

## Layer 5 — ANSI_training

Standard ANSI QWERTY layout for training/comparison. `tog 5` exits back.

---

## Layer 6 — MausUndCAD

CAD-optimized: full QWERTY on left, mouse buttons (`MB1`/`MB3`/`MB2`) on right thumb cluster. `tog 6` exits back.

---

## Layer 7 — CADnachMaus

Numpad overlay for CAD (numbers + operators on left hand). Active via `mo 7` from layer 6.

---

## Firmware Settings (`sofle.conf`)

```
CONFIG_EC11=y
CONFIG_EC11_TRIGGER_GLOBAL_THREAD=y
CONFIG_ZMK_SLEEP=y
CONFIG_ZMK_IDLE_SLEEP_TIMEOUT=900000   # 15 min
CONFIG_BT_CTLR_TX_PWR_PLUS_8=y
CONFIG_ZMK_KEYBOARD_NAME="SofleChoc"
CONFIG_ZMK_STUDIO=yes
CONFIG_ZMK_POINTING=y
```

---

## Custom Additions (not in upstream)

- **keymap-drawer** integration: auto-generated SVG visualizations via GitHub Actions
- **German Umlauts**: ö, ü, ä, ß via combos using AltGr (US-International layout)
- **Euro sign macro**: `€` via `LA(LC(N4))`
- **Sticky key macros**: `sticky_ss` (Super+Shift), `sticky_ssa` (Super+Alt+Shift)
- **Anführungszeichen macro**: Double-quote + space for German quotation
- **CAD layers** (6 & 7): Dedicated layers for CAD work with numpad and mouse
- **ANSI training layer** (5): Clean ANSI layout for reference
