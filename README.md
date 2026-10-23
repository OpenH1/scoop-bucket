# OpenH1 for Scoop

A [Scoop](https://scoop.sh) bucket for [OpenH1](https://openh1.com), Halo:
Combat Evolved recompiled from the decompiled Xbox game
([OpenH1/OpenH1](https://github.com/OpenH1/OpenH1)).

```powershell
scoop bucket add openh1 https://github.com/OpenH1/scoop-bucket
scoop install openh1
```

Then start **OpenH1** from the Start menu (or enter `openh1`).

## Why Scoop

The Windows build is not code-signed, so a zip downloaded with a browser
makes Windows SmartScreen say that it protected your PC (choose **More
info**, then **Run anyway**). Scoop's downloads do not carry the browser's
mark, so a Scoop install starts with no warning. Scoop checks each download
against the hash in [bucket/openh1.json](bucket/openh1.json).

## What it does

- Installs the latest release's `OpenH1-Windows.zip` in
  `~\scoop\apps\openh1`, with a Start menu shortcut and an `openh1` command.
- Keeps what is yours in `~\scoop\persist\openh1`, so that updates and
  uninstalls leave it: `config.toml`, `maps\`, `custom_maps\`, `mods\`,
  `screenshots\`, `crashes\` (unsent crash reports), and a host's
  `bans.txt`, `cheaters.txt` and `text_filter.txt`. Saved games are in
  `%APPDATA%\halo`, as with the zip. `scoop uninstall -p openh1` deletes
  the kept files too.
- Turns off the game's own updater (`update.auto = false` in `config.toml`,
  written at the first install): update with `scoop update openh1`.

## Game data

OpenH1 does not include the game. You need your own Xbox disc image
(`.iso` or `.xiso`) of Halo: Combat Evolved: at the first start the game
asks for it and copies its `maps` folder out of it (about 2 GB). Refer to
[openh1.com](https://openh1.com).

## Updates of the bucket

[Excavator](.github/workflows/excavator.yml) runs Scoop's `checkver` and
autoupdate every 6 hours: a new release (`build-<N>`) becomes the manifest's
version, with its hash. [Install](.github/workflows/install.yml) installs,
updates and uninstalls the manifest with Scoop on Windows and checks what it
keeps.

The manifest is under the game's licence, AGPL-3.0-or-later.
