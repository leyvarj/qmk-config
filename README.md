# Fifi Chocofi QMK Config

## Hardware

Fifi Chocofi (wired) with Pro Micro RP2040.
No RGB LEDs. No rotary encoders.
Use only 34 of 36 switches. The inner thumb slots on each half are unused.

Use `crkbd/rev1` with `converter: rp2040_ce`.

## Layers

![Fifi Choc Layout](fifi-choc/keymap.svg)

Configure four layers with a 3x5_3 split layout. Map Colemak-DH on the base layer
with mirrored homerow mod taps.

### Layer 0: Base

Map left modifiers `GUI_T`, `ALT_T`, `CTL_T`, `SFT_T` on the left hand.
Map right modifiers `RSFT_T`, `RCTL_T`, `RALT_T`, `RGUI_T` on the right hand.

Map the thumb cluster: ENT (left middle), MO(1) (left inner), MO(2)
(right inner), SPC (right middle).

### Layer 1: Symbols

Hold MO(1) with the left inner thumb to activate.

Place the symbol set on the right hand. Place shifted symbols on the left hand
in a 2-3-3 grid by column position. Map `! @ #` to the bottom row, `$ % ^` to the
middle row, and `& *` to the top row. Map Backspace to the right middle thumb.

### Layer 2: Numpad and Nav

Hold MO(2) with the right inner thumb to activate.

Map the numpad cluster to the left hand with navigation arrows on the
right hand home row. Map TAB to the left middle thumb for
field navigation while on this layer.

### Layer 3: Media and System

Press MO(3) from either layer 1 or layer 2 to access.

Map system controls to the left hand (ESC, Siri Assistant, Mission
Control). Map media controls to the right hand (brightness, volume,
mute, play/pause, track skip). Disable all thumb slots. Hold the layer key with thumbs to stay on L3.

## Tapping Configuration

| Setting                | Value   | Purpose                                  |
| ---------------------- | ------- | ---------------------------------------- |
| TAPPING_TERM           | 150     | Mod tap recognition window               |
| HOLD_ON_OTHER_KEY_PRESS | enabled | Require another key press to trigger mod |

## Build and Flash

```bash
qmk flash -kb crkbd/rev1 -km leyvarj -e CONVERT_TO=rp2040_ce
```

Double-tap reset on each half. Copy the uf2 file to the
RPI RP2 volume. Repeat for the other side.

## Files

| File                 | Contents                                                                                      |
| -------------------- | --------------------------------------------------------------------------------------------- |
| fifi-choc/keymap.c   | Keymap with four layers                                                                       |
| fifi-choc/config.h   | Configure tap hold and mod tap settings. Retain commented-out defines as dead code reference. |
| fifi-choc/rules.mk   | Feature flags for the build                                                                   |
| fifi-choc/keymap.svg | Keymap visualization                                                                          |

## Acknowledgments

- [QMK Firmware](https://qmk.fm/)
- [QMK CLI](https://github.com/qmk/qmk_cli)
- [Foostan](https://github.com/foostan/) — CRKBD designer
- [Pavel Glushkov](https://github.com/pashutk) — Chocofi designer
- [Ray Cheng](https://github.com/raychengy) — Original Fifi designer
- [keymap-drawer](https://github.com/caksoylar/keymap-drawer)
- [web app](https://keymap-drawer.streamlit.app/)
