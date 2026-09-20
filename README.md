# focus-rofi

Small Hyprland helper that waits for a Rofi window to appear and then focuses
it. It is intended to be started immediately before another script opens a Rofi
menu, working around cases where the menu does not receive focus.

## Build and install

```bash
nix build github:RevolunixOS/pkg-focus-rofi
nix profile install github:RevolunixOS/pkg-focus-rofi
```

## Usage

Run the helper in the background before opening Rofi:

```bash
focus-rofi &
rofi -show drun
```

## Requirements and behavior

- Hyprland and `hyprctl` must be available on the host.
- The script looks for a client whose class is exactly `Rofi`.
- It busy-waits until that client exists and has no timeout.
- The package currently does not wrap `hyprctl` into its runtime `PATH`.

Because of the busy loop, do not launch the helper unless a Rofi window will be
created immediately afterward.

## License

See [`LICENSE`](LICENSE).
