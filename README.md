# Numbat snap

[![numbat](https://snapcraft.io/numbat/badge.svg)](https://snapcraft.io/numbat)

Snap packaging for [Numbat](https://github.com/sharkdp/numbat), a scientific calculator and programming language with physical units and dimensional analysis.

Unofficial build, not affiliated with or endorsed by the Numbat project.

## Build

```bash
snapcraft pack
```

## Install and try

<a href="https://snapcraft.io/numbat"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install numbat                   # or a local build: ./numbat_1.24.0_*.snap --dangerous
sudo snap connect numbat:removable-media   # optional: /media, /mnt
numbat -e "8 km / (1 h + 25 min) -> mph"
numbat -e "100 EUR -> USD"                 # exchange rates are fetched from the ECB
numbat                                     # interactive session
```

Numbat's standard library is built into the binary, so nothing else needs to be installed.

### Configuration and history

Strict confinement gives the snap its own home folder, so files live under `~/snap/numbat/current` instead of `~`:

| File | Location |
|---|---|
| Config | `~/snap/numbat/current/.config/numbat/config.toml` |
| Init script | `~/snap/numbat/current/.config/numbat/init.nbt` |
| Custom modules | `~/snap/numbat/current/.config/numbat/modules/` |
| History | `~/snap/numbat/current/.local/share/numbat/history` |

Create a default config with `numbat --generate-config`.

## Known limitations

### Plots

`show(...)` on a plot (for example `show(line_plot(sin, 0, 2pi))`) does not work. Numbat writes the plot as an HTML file in the snap's private `/tmp` and runs `xdg-open` to show it in a browser. Strict confinement blocks this, so Numbat stops with `Could not find default application for HTML files` and `Permission denied`. All other calculations work.

## Update to a new upstream release

Change `source-tag` in `snap/snapcraft.yaml`, then rebuild.

## Automation

Builds, publishing, and dependency updates use [snap-automation](https://github.com/sidalit/snap-automation).

## License

The packaging is MIT-licensed (see `LICENSE`). Numbat is dual-licensed under MIT or Apache-2.0; its dependencies carry their own licenses.
