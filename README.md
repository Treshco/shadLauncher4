<!--
SPDX-FileCopyrightText: 2024 shadLauncher4 Project
SPDX-License-Identifier: GPL-2.0-or-later
-->

<h1 align="center">
  <br>
  <a href="https://shadlaunchers.com/"><img src="https://github.com/shadps4-emu/shadPS4/blob/main/.github/shadps4.png" width="220"></a>
  <br>
  <b>shadLauncher4</b>
  <br>
</h1>
<h1 align="center">
 <a href="https://discord.gg/agmZvBqwPv">
  <img src="https://img.shields.io/badge/Discord-shadLaunchers-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="shadLaunchers Discord">
</a>
 <a href="https://shadlaunchers.com">
        <img src="https://img.shields.io/badge/shadLaunchers-website-8A2BE2" width="150">
      <a title="Crowdin" target="_blank" href="https://crowdin.com/project/shadlauncher4"><img src="https://badges.crowdin.net/shadlauncher4/localized.svg"></a>
 <a href="https://github.com/shadLaunchers/shadLauncher4/stargazers">
        <img src="https://img.shields.io/github/stars/shadLaunchers/shadLauncher4" width="120">

</h1>
A Qt-based game launcher for shadPS4 emulator. shadLauncher4 manages your PS4 game library, tracks metadata and playtime, and launches titles with per-game or global emulator settings — without needing to touch the command line.

Translations can be done in crowdin page : https://crowdin.com/project/shadlauncher4
---
## Features

- **Game List** — List and grid view modes, adjustable icon sizes (Tiny/Small/Medium/Large), custom categories, search, hidden entries, tooltip notes per game, and gamelist export.
- **PKG Install** — Install PS4 application packages (.pkg) from the launcher, with a directory-selection dialog and support for installing multiple packages in one go.
- **ZArchive (.zar) Support** — Convert games and updates to ZArchive to save disk space, browse ZArchive contents without extracting, and extract archives back to a normal folder.
- **Trophy Viewer** — View earned trophies (uses a trophy key configured via the Crypto Key Manager).
- **DLC Viewer** — View a game's installed DLC.
- **SFO Viewer** — Inspect a game's parameter/SFO metadata.
- **npbind.dat Viewer** — Inspect a title's npbind data.
- **Cheats & Patches** — Browse and apply cheats and patches for supported games.
- **Game Compatibility** — View community compatibility reports for a game, or submit one.
- **Crypto Key Manager** — Manage keys used by the Trophy Viewer and other tools.
- **Network Host Overrides** — Redirect a game's network traffic to another server.
- **Setup Wizard** — Guided first-run setup.
- **User Accounts** — Manage multiple emulated user accounts.
- **Peripheral Emulation** — Manage Skylanders Portal of Power figures, Disney Infinity Base figures, and Lego Dimensions Toypad minifigures.
- **Controls Configuration** — Dedicated keyboard & mouse config GUI plus general controller/control settings.
- **Hotkeys** — Configurable hotkeys for the emulator.
- **Per-Game Custom Configuration** — Create a per-game configuration from global settings, edit it, or remove it; launch with global, current, or default settings.
- **Game Data Cleanup** — Delete a game's save data, shader cache, trophy data, DLC, or update/patch from the context menu.
- **Metadata Cache** — Caches name/serial/icon/size info per game, with a manual clear option.
- **Desktop Shortcuts** — Create a desktop shortcut for a game.
- **Settings** — General, Input, Graphics, Audio, Debug, Paths, and GUI settings categories.
- **Version Manager & Changelog** — View emulator version info and release changelogs in-app.
- **Auto-Update Checker** — Check for and install shadLauncher4 updates.
- **Logging** — In-app game log viewer, log presets, and log report submission.
- **UI Customization** — Selectable themes, background music player with hover-GIF playback toggle, adjustable toolbars/title bars, fullscreen toggle, and localization into 30+ languages via Crowdin.

---

Clone the repository with submodules:

```sh
git clone --recursive https://github.com/shadLaunchers/shadLauncher4.git
cd shadLauncher4

# If you cloned without --recursive:
git submodule update --init --recursive
```

---
## Building
### Windows

**Additional prerequisites:**

- [Visual Studio 2026](https://visualstudio.microsoft.com/)
- [LLVM/Clang](https://releases.llvm.org/)

**Steps:**

1. Configure:
   ```bat
   cmake --fresh -G Ninja ^
     -B build ^
     -DCMAKE_BUILD_TYPE=Release ^
     -DCMAKE_C_COMPILER=clang-cl ^
     -DCMAKE_CXX_COMPILER=clang-cl
   ```
   If Qt is not found automatically, add `-DCMAKE_PREFIX_PATH="C:/Qt/6.10.0/msvc2022_64"` (adjust to your install path).
2. Build:
   ```bat
   cmake --build build --config Release --parallel
   ```
---

### Linux
**Arch Linux**
```sh
sudo pacman -S --needed \
  clang cmake ninja \
  qt6-base qt6-tools qt6-multimedia \
  openssl \
  vulkan-headers vulkan-icd-loader \
  alsa-lib libpulse \
  mesa
```

**Debian/Ubuntu**
```sh
sudo apt-get install -y \
  clang cmake ninja-build \
  libssl-dev \
  libvulkan-dev \
  libasound2-dev libpulse-dev \
  libgl1-mesa-dev \
  libxcb-cursor-dev
```
**Steps:**
1. Configure:
   ```sh
   cmake --fresh -G Ninja \
     -B build \
     -DCMAKE_BUILD_TYPE=Release \
     -DCMAKE_C_COMPILER=clang \
     -DCMAKE_CXX_COMPILER=clang++
   ```
2. Build:
   ```sh
   cmake --build build --parallel $(nproc)
   ```
3. Run:
   ```sh
   ./build/shadLauncher4
   ```
