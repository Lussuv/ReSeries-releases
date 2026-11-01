# ReSeries

**Peripheral control and an audio mixer for KDE Plasma on Linux.**

ReSeries manages headsets, mice and keyboards from the desktop: battery, sidetone, auto power-off, equalizer and more. It also ships with **SoundTry**, a PipeWire mixer that has per-app channels, ChatMix support and a microphone effects chain (echo cancellation, noise suppression, noise gate, EQ, compressor and limiter). A guided assistant sets up the microphone chain from measurements.

This repository only hosts the release packages. Grab the latest one from **[Releases](../../releases)**.

---

## Supported systems

| Distribution | Package |
|---|---|
| Arch Linux and derivatives (CachyOS, EndeavourOS, …) | `reseries-<version>-x86_64.pkg.tar.zst` |
| Ubuntu / Kubuntu 24.04+, Debian 13+ | `reseries_<version>_amd64.deb` |

ReSeries needs **PipeWire** with **WirePlumber**. It supports KDE Plasma 5.27 and Plasma 6, and the installer picks the matching widget variant automatically.

## Supported devices

| Device | Features | Status |
|---|---|---|
| SteelSeries Arctis 7+ | Battery, ChatMix, sidetone, auto power-off, equalizer | experimental |

Experimental devices are hidden by default. To show them, go to **Settings → Experimental devices**.

---

## Installation

**Arch Linux**

```sh
sudo pacman -U reseries-*.pkg.tar.zst
