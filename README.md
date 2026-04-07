# Dytroxx's Sofle Keymap

Custom keymap for the [Sofle v1](https://github.com/josefadamcik/SofleKeyboard) split keyboard, featuring 6 layers, German locale support, smart backspace/delete, OS-aware custom keycodes, and rotary encoder integration.

## Features

- **6 Layers** — QWERTY (default), Lower (symbols/F-keys), Raise (navigation), LOC (German locale), Adjust (system/media), Gaming
- **Tri-Layer** — Holding Lower + Raise simultaneously activates the Adjust layer
- **Smart Backspace/Delete** — `BsDel` sends Backspace normally; hold Shift and it sends Delete instead
- **German Locale Layer (LOC)** — Momentary layer (hold top-left key) for Umlauts (Ä, Ö, Ü), Eszett (ß), and Euro sign (€) via `RALT` compose sequences
- **OS Toggle (`CG_TOGG`)** — Swaps Ctrl/GUI so custom keycodes (Prev/Next Word, Line Start/End, Copy, Paste, etc.) work correctly on both macOS and Windows/Linux
- **Gaming Layer** — Dedicated layer with Space on the left thumb (for WASD gaming) and no accidental layer-switching keys
- **Rotary Encoders** — Left encoder: scroll Left/Right (or Prev/Next Track with Shift). Right encoder: scroll Up/Down (or Vol Up/Down with Shift)
- **Split Keyboard** — Full split support with USB detection, synced layer state, LED state, and matrix mirroring
- **KeyPeek Integration** — Live on-screen overlay via the [`srwi/keypeek_layer_notify`](https://github.com/srwi/qmk-modules) module
- **VIA Support** — Runtime keymap editing via VIA
- **WPM Tracking** — Words-per-minute counter (synced to both halves)
- **OLED Display** — Enabled at the keyboard level

## Layers

### QWERTY (Default)

```
 ,-----------------------------------------.                    ,-----------------------------------------.
 | Esc  |   1  |   2  |   3  |   4  |   5  |                    |   6  |   7  |   8  |   9  |   0  |BsDel |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 | _LOC |   Q  |   W  |   E  |   R  |   T  |                    |   Y  |   U  |   I  |   O  |   P  |  `   |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 | Caps |   A  |   S  |   D  |   F  |   G  |-------.    ,-------|   H  |   J  |   K  |   L  |   ;  |  '   |
 |------+------+------+------+------+------| Tog_OS|    |QWERTY |------+------+------+------+------+------|
 |LShift|   Z  |   X  |   C  |   V  |   B  |-------|    |-------|   N  |   M  |   ,  |   .  |   /  |  \   |
 `-----------------------------------------/       /     \      \-----------------------------------------'
            | LGUI | LAlt | LCTR | LOWER |/ Enter /       \Space \  |RAISE | RCTR | RAlt | RGUI |
            |      |      |      |      |/       /         \      \ |      |      |      |      |
            `----------------------------------'           '------''---------------------------'
```

- `_LOC` (top-left) is a momentary key — hold it to activate the German locale layer
- `BsDel` is Smart Backspace/Delete (Backspace normally, Delete when Shift is held)
- `Tog_OS` toggles Ctrl/GUI swap for macOS compatibility
- `QWERTY` (right-side encoder column key) resets to the default QWERTY layer

### Lower (Symbols & F-Keys)

Activated by holding `LOWER`.

```
 ,-----------------------------------------.                    ,-----------------------------------------.
 |      |  F1  |  F2  |  F3  |  F4  |  F5  |                    |  F6  |  F7  |  F8  |  F9  | F10  | F11  |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 |  `   |   1  |   2  |   3  |   4  |   5  |                    |   6  |   7  |   8  |   9  |   0  | F12  |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 |      |   !  |   @  |   #  |   $  |   %  |-------.    ,-------|   ^  |   &  |   *  |   (  |   )  |  |   |
 |------+------+------+------+------+------|       |    |       |------+------+------+------+------+------|
 |Shift |   =  |   -  |   +  |   {  |   }  |-------|    |-------|   [  |   ]  |   ;  |   :  |   \  |Shift |
 `-----------------------------------------/       /     \      \-----------------------------------------'
            | LGUI | LAlt | LCTR | LOWER |/ Enter /       \Space \  |RAISE | RCTR | RAlt | RGUI |
            |      |      |      |      |/       /         \      \ |      |      |      |      |
            `----------------------------------'           '------''---------------------------'
```

### Raise (Navigation)

Activated by holding `RAISE`.

```
 ,-----------------------------------------.                    ,-----------------------------------------.
 |      |      |      |      |      |      |                    |      |      |      |      |      |      |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 |      | Ins  | Pscr | Menu |      |      |                    | PgUp | PWrd |  Up  | NWrd |DLine | Bspc |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 |      | LAlt | LCtl |LShft |      | Caps |-------.    ,-------| PgDn | Left | Down |Right |  Del | Bspc |
 |------+------+------+------+------+------|       |    |       |------+------+------+------+------+------|
 |Shift | Undo | Cut  | Copy |Paste |      |-------|    |-------|      | Home |      | End  |      |Shift |
 `-----------------------------------------/       /     \      \-----------------------------------------'
            | LGUI | LAlt | LCTR | LOWER |/ Enter /       \Space \  |RAISE | RCTR | RAlt | RGUI |
            |      |      |      |      |/       /         \      \ |      |      |      |      |
            `----------------------------------'           '------''---------------------------'
```

- `PWrd` / `NWrd` — Previous/Next word (Ctrl+Left/Right, or Alt+Left/Right on macOS)
- `DLine` — Delete line (Ctrl+Backspace)
- `Home` / `End` — Line start/end (Cmd+Left/Right on macOS)
- `Undo` / `Cut` / `Copy` / `Paste` — OS-aware shortcuts (Ctrl or Cmd depending on `CG_TOGG`)

### LOC (German Locale Overlay)

Activated by holding `_LOC` on the QWERTY layer. Provides German characters via `RALT` compose sequences.

```
 ,-----------------------------------------.                    ,-----------------------------------------.
 | Esc  |   1  |   2  |   3  |   4  |   5  |                    |   6  |   7  |   8  |   9  |   0  |BsDel |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 | Tab  |   Q  |   W  |   €  |   R  |   T  |                    |   Y  |   Ü  |   I  |   Ö  |   P  |  `   |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 | Caps |   Ä  |   ß  |   D  |   F  |   G  |-------.    ,-------|   H  |   J  |   K  |   L  |   Ö  |  '   |
 |------+------+------+------+------+------| Tog_OS|    |QWERTY |------+------+------+------+------+------|
 |LShift|   Z  |   X  |   C  |   V  |   B  |-------|    |-------|   N  |   M  |   ,  |   .  |   /  |  \   |
 `-----------------------------------------/       /     \      \-----------------------------------------'
            | LGUI | LAlt | LCTR | LOWER |/ Enter /       \Space \  |RAISE | RCTR | RAlt | RGUI |
            |      |      |      |      |/       /         \      \ |      |      |      |      |
            `----------------------------------'           '------''---------------------------'
```

- `Ä` = `RALT(Q)`, `Ö` = `RALT(P)`, `Ü` = `RALT(Y)`, `ß` = `RALT(S)`, `€` = `RALT(5)`
- Requires a US International keyboard layout or similar compose-key setup on the OS

### Adjust (System & Media)

Activated by holding `LOWER` + `RAISE` simultaneously (tri-layer).

```
 ,-----------------------------------------.                    ,-----------------------------------------.
 |      |      |      |      |      |      |                    |      |      |      |      |      |      |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 | BOOT |      |QWERTY|      |Tog_OS| GAME |                    |      |      |      |      |      |      |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 |      |      |Tog_OS|      |      |      |-------.    ,-------|      | Vol- | Mute | Vol+ |      |      |
 |------+------+------+------+------+------|       |    |       |------+------+------+------+------+------|
 |      |      |      |      |      |      |-------|    |-------|      | Prev | Play | Next |      |      |
 `-----------------------------------------/       /     \      \-----------------------------------------'
            | LGUI | LAlt | LCTR | LOWER |/ Enter /       \Space \  |RAISE | RCTR | RAlt | RGUI |
            |      |      |      |      |/       /         \      \ |      |      |      |      |
            `----------------------------------'           '------''---------------------------'
```

- `BOOT` — Enter bootloader (for flashing)
- `QWERTY` — Set QWERTY as default layer
- `GAME` — Set Gaming as default layer
- `Tog_OS` — Toggle Ctrl/GUI swap
- Media controls: Vol-/Mute/Vol+, Prev/Play/Next

### Gaming

Activated via the Adjust layer (`GAME` key). Persists as the default layer until switched back.

```
 ,-----------------------------------------.                    ,-----------------------------------------.
 | Esc  |   1  |   2  |   3  |   4  |   5  |                    |   6  |   7  |   8  |   9  |   0  | Bspc |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 | Tab  |   Q  |   W  |   E  |   R  |   T  |                    |   Y  |   U  |   I  |   O  |   P  |  `   |
 |------+------+------+------+------+------|                    |------+------+------+------+------+------|
 | Caps |   A  |   S  |   D  |   F  |   G  |-------.    ,-------|   H  |   J  |   K  |   L  |   ;  |  '   |
 |------+------+------+------+------+------|       |    |       |------+------+------+------+------+------|
 |LShift|   Z  |   X  |   C  |   V  |   B  |-------|    |-------|   N  |   M  |   ,  |   .  |   /  |RShift|
 `-----------------------------------------/       /     \      \-----------------------------------------'
            | LGUI | LAlt | LCTR | LOWER |/ Space /       \Enter \  |RAISE | RCTR | RAlt | RGUI |
            |      |      |      |      |/       /         \      \ |      |      |      |      |
            `----------------------------------'           '------''---------------------------'
```

- Space is on the left thumb (natural for WASD)
- Enter moved to the right thumb
- No LOC layer key or OS toggle — clean layout for gaming
- To switch back: Lower + Raise (Adjust) → `QWERTY`

## Rotary Encoders

| Encoder | Normal         | With Shift Held   |
|---------|----------------|-------------------|
| Left    | Arrow Left/Right | Prev/Next Track |
| Right   | Arrow Up/Down  | Volume Down/Up    |

## Custom Keycodes

| Keycode      | Description                                                            |
|--------------|------------------------------------------------------------------------|
| `KC_BSPC_DEL`| Backspace; Delete when Shift is held                                  |
| `KC_LOWER`   | Hold for Lower layer; participates in tri-layer (Lower+Raise=Adjust)  |
| `KC_RAISE`   | Hold for Raise layer; participates in tri-layer (Lower+Raise=Adjust)  |
| `KC_ADJUST`  | Hold for Adjust layer                                                 |
| `KC_PRVWD`   | Previous word (Ctrl+Left / Alt+Left on macOS)                         |
| `KC_NXTWD`   | Next word (Ctrl+Right / Alt+Right on macOS)                           |
| `KC_LSTRT`   | Line start (Home / Cmd+Left on macOS)                                 |
| `KC_LEND`    | Line end (End / Cmd+Right on macOS)                                   |
| `KC_DLINE`   | Delete line/word backward (Ctrl+Backspace)                            |
| `KC_QWERTY`  | Set QWERTY as default layer (persistent)                              |
| `KC_GAMING`  | Set Gaming as default layer (persistent)                              |
| `KC_LAYER`   | Activates Lower; with Shift resets to QWERTY (defined but unused)     |

## Enabled Features

| Feature       | Status  | Notes                                  |
|---------------|---------|----------------------------------------|
| Bootmagic     | Enabled | From keyboard defaults                 |
| Encoder       | Enabled | Two rotary encoders                    |
| Extrakey      | Enabled | Media/system key support               |
| Mousekey      | Enabled | From keyboard defaults                 |
| NKRO          | Enabled | N-key rollover                         |
| OLED          | Enabled | From keyboard defaults                 |
| RAW HID       | Enabled | Required for KeyPeek                   |
| VIA           | Enabled | Runtime keymap editing                 |
| WPM           | Enabled | Words-per-minute tracking              |

## Build & Flash

```bash
# Compile
qmk compile -kb sofle/rev1 -km dytroxxkeymap

# Flash (connect each half individually via USB)
qmk flash -kb sofle/rev1 -km dytroxxkeymap

# Generate keyboard_info.json (for KeyPeek)
qmk info -kb sofle/rev1 -km dytroxxkeymap -m -f json > keyboards/sofle/keymaps/dytroxxkeymap/keyboard_info.json
```

> **Note:** Both halves must be flashed with the same firmware. Connect each half via USB separately and flash.

## KeyPeek Setup

This keymap includes the [`srwi/keypeek_layer_notify`](https://github.com/srwi/qmk-modules) QMK module for live layer overlay via [KeyPeek](https://github.com/srwi/keypeek).

1. The module is already configured in `keymap.json`
2. `RAW_ENABLE` and `VIA_ENABLE` are set in `rules.mk`
3. After flashing, run KeyPeek and select your Sofle
4. When prompted, load the `keyboard_info.json` from this keymap directory

## File Structure

```
keyboards/sofle/keymaps/dytroxxkeymap/
├── config.h              # Split keyboard defines, layer count
├── keymap.c              # Layers, custom keycodes, encoder logic
├── keymap.json           # QMK module references (keypeek)
├── keyboard_info.json    # Generated layout info for KeyPeek
├── rules.mk              # Enabled features (WPM, RAW, VIA)
└── README.md             # This file
```

## License

GPL-2.0-or-later. See [LICENSE](https://www.gnu.org/licenses/gpl-2.0.html).
