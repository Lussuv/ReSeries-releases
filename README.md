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
| SteelSeries Aerox 3 Wireless Gen 2 | Battery, charging, DPI steps, lift-off distance, polling rate, power saving, lighting, acceleration, angle snapping, button mapping | experimental |
| SteelSeries Apex 3 TKL | Brightness, colour of the 8 lighting zones | experimental |
| Glorious Model O 2 PRO Wireless | Battery, charging, DPI steps, polling rate, Motion Sync, debounce, button mapping | experimental |
| Poly Voyager Focus 2 (BT700 dongle or USB-C) | Battery, charging, ANC position, mute state, sidetone, call and mute prompts, wear sensor, HD Voice, anti-startle, noise exposure limit, factory reset | experimental |

Experimental devices are hidden by default. To show them, go to **Settings → Experimental devices**.

---

## Installation

**Arch Linux**

```sh
sudo pacman -U reseries-*.pkg.tar.zst
```

**Ubuntu / Debian**

```sh
sudo apt install ./reseries_*_amd64.deb
```

Log out and back in once afterwards, or start the services right away:

```sh
systemctl --user start reseries-daemon soundtry-engine
```

Then open **ReSeries** from the application menu. The **ReSeries** and **SoundTry** widgets appear in the system tray after the next login (or after restarting Plasma); you can hide or remove them there as usual.

> SoundTry registers itself as the default output ("SoundTry") and input ("SoundTry Mic"). Your previous devices are restored when the engine stops.

## Updates

ReSeries checks this repository for new versions and notifies you. Installing an update asks for your password once. Before installing, ReSeries verifies the package signature and refuses anything that is unsigned, tampered with or older than the installed version.

## Verifying a download

Every package comes with a [minisign](https://jedisct1.github.io/minisign/) signature (`.minisig`). To check a download by hand:

```sh
minisign -Vm reseries_<version>_amd64.deb -P RWSDb+4tFvkgfQIFT9poYlfM+fSotet80wYLWEoONw/bRwSHrfB77I61
```

The trusted comment names the exact file it belongs to.

## Uninstall

```sh
sudo pacman -R reseries     # Arch
sudo apt remove reseries    # Ubuntu / Debian
```

Your settings stay in `~/.config/reseries` and can be deleted by hand.

---

## Known limitations

- Echo cancellation on Ubuntu 24.04 uses the older WebRTC library that ships with the system. It works, but suppresses echo less strongly than on Arch or Debian 13.
- ReSeries has been tested mainly on Arch with Plasma 6. Feedback from Kubuntu 24.04 (Plasma 5.27, WirePlumber 0.4) is very welcome.

## License & credits

ReSeries is its own implementation. Protocol knowledge from projects such as HeadsetControl served as a reference only, no code was taken from them. Third-party licenses are installed with the package under `/usr/share/licenses/reseries/`.

The user interface is built with [Slint](https://slint.dev).

<a href="https://slint.dev">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/slint-ui/slint/master/logo/MadeWithSlint-logo-dark.svg">
    <img alt="Made with Slint" src="https://raw.githubusercontent.com/slint-ui/slint/master/logo/MadeWithSlint-logo-light.svg" height="60">
  </picture>
</a>
