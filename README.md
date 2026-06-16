# ttf-mscorefonts-installer (Universal Windows 11 Edition)

A modernized, offline-first Debian package for high-fidelity Microsoft Windows 11 font emulation on Linux.

## 🚀 Overview
This repository provides the packaging logic to build a native Debian `.deb` installer that brings the complete Windows 11 typography experience to your Linux desktop. Unlike the original package, this version is designed for a **local-only, native-payload** installation.

## ✨ Key Features
*   **DPkg Native Payload**: Fonts are bundled directly inside the `.deb` file. No scripts download anything during installation. This ensures a 100% reliable, offline, and atomic install.
*   **Zero Dependencies**: Completely removed `wget`, `cabextract`, and `ca-certificates`.
*   **Perfect Windows 11 Emulation**:
    *   **UI & Sans-Serif**: Maps `system-ui` and `sans-serif` to **Segoe UI Variable** and **Segoe UI**.
    *   **Emoji Superiority**: Full **Segoe UI Emoji** support with clean fallback logic that doesn't interfere with text.
    *   **Modern Math**: Maps `math` to **Cambria Math** (Unicode-compliant) instead of the outdated Symbol font.
    *   **Expanded Categories**: Mapped **cursive** (Comic Sans, Segoe Script, etc.), **fantasy** (Impact, Juice ITC), and **symbol** (Segoe UI Symbol, Webdings, Wingdings) to their official Windows counterparts.
    *   **PostScript Fallbacks**: Soft-aliasing for `Helvetica` (Arial), `Times` (Times New Roman), and `Courier` (Courier New).
*   **Clean System**: Includes logic to automatically purge legacy state files and stale configs from older installer versions.

## 🛠️ Installation

### 1. Prepare the Fonts
Copy your collection of Windows 11 fonts (typically from `C:\Windows\Fonts`) into the `msfonts/` directory.
The build system supports:
*   `.ttf` / `.TTF` (TrueType)
*   `.ttc` / `.TTC` (TrueType Collection)
*   `.otf` / `.OTF` (OpenType)

### 2. Build the Package
From the root of the repository:
```bash
dpkg-buildpackage -us -uc -b
```

### 3. Install
Install the resulting package:
```bash
sudo dpkg -i ../ttf-mscorefonts-installer_3.8.2_all.deb
```

### 4. Or Install from GitHub Releases

Download the latest prebuilt package from the GitHub Releases page:

```bash
wget https://github.com/relvinarsenio/ttf-mscorefonts-installer/releases/download/release-uw11/ttf-mscorefonts-installer_uw11_all.deb
sudo dpkg -i ttf-mscorefonts-installer_uw11_all.deb
```

## ⚖️ Licensing
The packaging scripts and metadata are provided under their respective open-source licenses.

**IMPORTANT**: The Microsoft font files themselves are proprietary. You are responsible for acquiring legally licensed copies of these fonts for your own personal use. Redistribution of the resulting `.deb` package may be subject to Microsoft's EULA.
