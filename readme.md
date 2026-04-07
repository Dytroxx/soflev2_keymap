# Dytroxx Keymap for Sofle v2

Custom QMK keymap for the Sofle split keyboard, designed for dual Mac/Windows use with German locale support.

## Layers

### QWERTY (Default)

Standard QWERTY layout with:
- **Smart Backspace/Delete**: Top-right key sends Backspace, or Delete when Shift is held
- **LOC layer**: Hold top-left key to access German umlauts (ä, ö, ü, ß, €)
- **CG Toggle**: Left encoder button swaps Ctrl/GUI for Mac ↔ Windows switching

```
 ,-----------------------------------------.                    ,-----------------------------------------.
 | Esc  |   1  |   2  |   3  |   4  |   5  |                    |   6  |   7  |   8  |   9  |   0  |BS/Del|
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 | _LOC |   Q  |   W  |   E  |   R  |   T  |                    |   Y  |   U  |   I  |   O  |   P  |  `   |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 | Caps |   A  |   S  |   D  |   F  |   G  |-------.    ,-------|   H  |   J  |   K  |   L  |   ;  |  '   |
 |------+------+------+------+------+------|CG_Tog |    |QWERTY |------+------+------+------+------+------|
 |LShift|   Z  |   X  |   C  |   V  |   B  |-------|    |-------|   N  |   M  |   ,  |   .  |   /  |  \   |
 `-----------------------------------------/       /     \      \-----------------------------------------'
            | LGUI | LAlt | LCtl | LOWER |/ Enter /       \Space \  |Raise | RCtl | RAlt | RGUI |
            `----------------------------------'           '------''---------------------------'
```

### LOWER (Hold left thumb)

F-keys, number row, and symbols.

### RAISE (Hold right thumb)

Navigation, clipboard operations (Undo/Cut/Copy/Paste), arrow keys.

### LOC (Hold top-left key)

German locale overlay — remaps select keys to umlauts via `RALT()`:
- **E** → € (`RALT+5`)
- **U** → ü (`RALT+Y`)
- **O** → ö (`RALT+P`)
- **A** → ä (`RALT+Q`)
- **S** → ß (`RALT+S`)

> Requires US-International or EurKEY keyboard layout on the OS side.

### ADJUST (Hold LOWER + RAISE)

System controls:
- **QK_BOOT** — Enter bootloader (top-left)
- **KC_QWERTY** — Switch to QWERTY default layer
- **KC_GAMING** — Switch to Gaming default layer
- **CG_TOGG** — Toggle Ctrl/GUI swap (Mac ↔ Windows)
- **Volume** / **Media** controls on right side

### GAMING

Clean gaming layout — no accidental layer switches on the left side:
- Space on left thumb, Enter on right (swapped from QWERTY)
- No CG_TOGG or LOC layer keys
- LOWER/RAISE still accessible for F-keys and navigation

## Encoders

| Encoder | Normal      | Shift held  |
|---------|-------------|-------------|
| Left    | ← / →       | Prev / Next track |
| Right   | ↑ / ↓       | Vol Down / Vol Up |

## OLED Displays

| Half   | Content |
|--------|---------|
| Master | Layer name, OS mode (macOS/Win), WPM counter, Caps Lock |
| Slave  | Hovering banana animation 🍌 |

## Features

| Feature          | Status  |
|------------------|---------|
| OLED             | Enabled |
| Encoder          | Enabled |
| WPM counter      | Enabled |
| Console          | Enabled |
| Extra keys       | Enabled |

## Build

```bash
qmk compile -kb sofle -km dytroxxkeymap
qmk flash -kb sofle -km dytroxxkeymap
```

Builds as `sofle/rev1` target (default for the `sofle` keyboard).

## Mac / Windows Switching

Use **CG_TOGG** (on QWERTY layer left encoder button, or ADJUST layer) to swap Ctrl and GUI. This makes the keyboard work naturally on both operating systems. The OLED master display shows the current OS mode.
