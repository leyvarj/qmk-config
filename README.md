# Fifi Chocofi QMK Config

## Hardware

Fifi Chocofi (wired) with Pro Micro RP2040.
The board has no RGB LEDs and no rotary encoders.
Only 34 of the 36 switches are used. The outer columns on both
halves are disabled.

The board uses `crkbd/rev1` with `converter: promicro_rp2040`.

## Layers

![Fifi Choc Layout](fifi-choc/keymap.svg)

Four layers with 3x5_3 split layout. The base layer is QWERTY
with mirrored homerow mod taps. The outer column on each side
is unused (`XXXXXXX`).

### Layer 0: Base

Left hand uses left modifiers: `GUI_T`, `ALT_T`, `CTL_T`, `SFT_T`.
Right hand uses right modifiers: `RSFT_T`, `RCTL_T`, `RALT_T`, `RGUI_T`.

Thumb cluster: ENT (left middle), MO(1) (left inner), MO(2)
(right inner), SPC (right middle).

### Layer 1: Symbols

Activated by holding MO(1) with the left inner thumb.

The right hand carries the symbol set. The left hand covers
the shifted symbol group in a 3x3 grid: `! @ #` on the bottom
row, `$ % ^` on the middle row, `& *` on the top row.
Backspace is mapped to the right middle thumb.

### Layer 2: Numpad and Nav

Activated by holding MO(2) with the right inner thumb.

Numpad cluster on the left hand with navigation arrows on the
right hand home row. TAB replaces the left middle thumb for
field navigation while on this layer.

### Layer 3: Media and System

Accessed by pressing MO(3) from either layer 1 or layer 2.

System controls on the left hand (ESC, Siri Assistant, Mission
Control). Media controls on the right hand (brightness, volume,
mute, play/pause, track skip). Thumbs are occupied holding the
layer key to stay on L3 so all thumb slots are disabled.

## Tapping Configuration

| Setting         | Value   | Purpose                                  |
| --------------- | ------- | ---------------------------------------- |
| TAPPING_TERM    | 150     | Mod tap recognition window               |
| QUICK_TAP_TERM  | 0       | Repeated taps always send tap            |
| PERMISSIVE_HOLD | enabled | Rolling to the next key triggers the mod |

## Disabled Features

RGB lighting and encoder map support are disabled in rules.mk
to save firmware space. The commented out defines in config.h
are dead code and kept only for reference.

## Build and Flash

```bash
qmk flash -kb crkbd/rev1 -km leyvarj -e CONVERT_TO=promicro_rp2040
```

Double tap reset on each half then copy the uf2 file to the
RPI RP2 volume. Repeat for the other side.

## Files

| File                  | Contents                                       |
| --------------------- | ---------------------------------------------- |
| fifi-choc/keymap.c    | Keymap with four layers                        |
| fifi-choc/config.h    | Tap hold and mod tap configuration             |
| fifi-choc/rules.mk    | Feature flags for the build                    |
| fifi-choc/keymap.json | Full keymap JSON (keyboard, converter, layers) |
| fifi-choc/keymap.yaml | Parsed keymap for keymap-drawer                |
| fifi-choc/keymap.svg  | Keymap visualization                           |

## Acknowledgments

- [QMK Firmware](https://qmk.fm/) - The open-source keyboard firmware that powers this board.
- [QMK CLI](https://github.com/qmk/qmk_cli) - Command-line tool for building, flashing, and converting keymaps.
- [Foostan](https://github.com/foostan/) - Designer of the Corne (CRKBD) keyboard.
- [Pavel Glushkov](https://github.com/pashutk) - Designer of the Chocofi.
- [Ray Cheng](https://github.com/raychengy) - Designer of the original Fifi keyboard.
- [keymap-drawer](https://github.com/caksoylar/keymap-drawer) - Visualizes keymaps with support for hold-taps, combos, and split layouts ([web app](https://keymap-drawer.streamlit.app/)).
