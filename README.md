# wvkbd-centered

Arch package of [wvkbd](https://git.sr.ht/~proycon/wvkbd) 0.21 with one
addition: `--dock center`, which shows a narrower keyboard centred at the
bottom of the screen.

Upstream `--width` / `--ratio` only take effect with `--dock left|right`.
With the default full-width dock, `--width` makes the keyboard invisible.
`center-dock.patch` adds a `DOCK_CENTER` mode. The layer surface is anchored
only to the bottom edge, so the compositor centres it horizontally. It still
reserves an exclusive zone, so windows shrink above it instead of being
covered.

```sh
wvkbd-mobintl --dock center --width 1100 -L 250
wvkbd-mobintl --dock center --ratio 0.6
```

## Build / install

```sh
makepkg -si      # provides/conflicts wvkbd, so it replaces the AUR package
```

When upstream releases a new version: bump `pkgver`, update the tarball
checksum, check that the patch still applies, and rebuild. paru does not track
this package.

## Example: hidden at login, toggled from a panel button

- Autostart: `wvkbd-mobintl --hidden --no-popup -L 250 --dock center --width 1100`
- Panel launcher: `pkill -RTMIN -x wvkbd-mobintl || exec wvkbd-mobintl --no-popup -L 250 --dock center --width 1100`

wvkbd is GPL-3.0; this patch is under the same licence.
