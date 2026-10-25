<div align="center">

<img src="snap/gui/numbat.png" alt="Numbat logo" width="128" />

# Numbat

**Calculate with physical units and dimensional analysis.**

[![numbat](https://snapcraft.io/numbat/badge.svg)](https://snapcraft.io/numbat)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [Numbat](https://github.com/sharkdp/numbat), a scientific calculator and programming language with built-in unit conversions.

</div>

---

## Getting Started

<a href="https://snapcraft.io/numbat"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install numbat
numbat
```

Run a calculation directly with `numbat -e "8 km / (1 h + 25 min) -> mph"`. The standard library is included; currency conversions fetch exchange rates from the European Central Bank.

## Configure

There are no `snap set` options. Create a default application configuration with:

```bash
numbat --generate-config
```

| File | Location |
|---|---|
| Configuration | `~/snap/numbat/current/.config/numbat/config.toml` |
| Startup script | `~/snap/numbat/current/.config/numbat/init.nbt` |
| Custom modules | `~/snap/numbat/current/.config/numbat/modules/` |
| History | `~/snap/numbat/current/.local/share/numbat/history` |

These locations belong to the snap; an existing host configuration is not read automatically. To open scripts on removable drives under `/media` or `/mnt`:

```bash
sudo snap connect numbat:removable-media
```

## Limitations

Opening plots with `show(...)` does not work: plot HTML is written into the snap's private temporary directory and cannot be opened in the host browser. This does not prevent normal calculations or scripts from running.

## Build

```bash
git clone https://github.com/sidalit/numbat-snap.git
cd numbat-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/numbat-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/sharkdp/numbat/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/numbat-snap/blob/main/LICENSE).
