# Lily58 ZMK Config

Personal ZMK firmware config for a Lily58 (nRF52840 / nice!nano v2, built-in
SSD1306 OLED, wireless). Built for macOS, coding, Excel, and mouse-free
browsing/YouTube.

Pinned to ZMK release `v0.3.0` for build stability (see `config/west.yml`).

## Layers

- **default_layer** — QWERTY. Home row mods on both hands: hold `A/S/D/F`
  (right hand mirrors on `J/K/L/;`) for Shift/Ctrl/Alt/Gui, tap for the
  letter. `mo 1` / `mo 2` thumb keys hold Lower/Raise.
- **lower_layer** — numbers row shifted to F-keys, symbols laid out for
  coding (`- = _ + [ ] { } | : " < > ?` etc).
- **raise_layer** — arrow keys, Home/End/PgUp/PgDn, mouse click/scroll
  (`&mkp`/`&msc`) for mouse-free browsing, volume keys, full-screen
  screenshot (`Cmd+Shift+3`, `LG(LS(N3))` — change to `LS(LG(N4))` for
  selection-area screenshot if you prefer that instead).
- **adjust_layer** — Bluetooth profile select/clear/disconnect, F11/F12.
  Reached by holding Lower + Raise together.

## Building

GitHub Actions builds automatically on push (see
`.github/workflows/build.yml`, calls ZMK's reusable
`build-user-config.yml` workflow). Firmware `.uf2` files show up as a
build artifact on the Actions run — download, then drag onto the
`NICENANO` USB mass-storage drive (put the half in bootloader mode by
double-tapping reset) for left and right halves separately.

## Local changes

Edit `config/lily58.keymap` for layout changes, `config/lily58.conf` for
Kconfig options, `build.yaml` to change which board/shield combos get
built.

## Flashing checklist

1. Push changes to GitHub.
2. Wait for the Actions build to go green.
3. Download the `firmware` artifact zip from the run.
4. Put one half into bootloader mode (double-tap reset button) — it
   shows up as a `NICENANO` drive.
5. Drag the matching `lily58_left-nice_nano_v2-zmk.uf2` or
   `lily58_right-nice_nano_v2-zmk.uf2` onto that drive.
6. Repeat for the other half.
