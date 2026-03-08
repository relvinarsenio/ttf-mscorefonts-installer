# ttf-mscorefonts-installer (Local BYOF Edition)

This is a heavily modified, offline-first installer for the Microsoft TrueType Core Fonts for Debian/Ubuntu systems.

## Features
* **Bring Your Own Files (BYOF)**: This installer does NOT download fonts from the internet. It requires you to provide your own original Windows font files (e.g., from a Windows 11 installation) due to Microsoft licensing restrictions.
* **No Network Dependencies**: Removed dependencies on `wget` and `cabextract`.
* **Symlink Optimization**: Installs fonts using symbolic links to save disk space.
* **Advanced Fontconfig Priorities**: Includes custom fontconfig rules to perfectly emulate the Windows font fallback experience:
  * Maps `sans-serif` to **Arial**.
  * Maps `serif` to **Times New Roman**.
  * Maps `monospace` to **Consolas** and **Courier New**.
  * Provides perfect emoji fallback using **Segoe UI Emoji** without breaking standard text rendering.

## Installation Instructions

1. **Obtain the Fonts**: Copy the 196 core TrueType fonts from a Windows installation (e.g., `C:\Windows\Fonts`) into the `msfonts/` directory of this repository.
2. **Build the Package**:
   ```bash
   dpkg-buildpackage -us -uc -b
   ```
3. **Install the Package**:
   ```bash
   sudo dpkg -i ../ttf-mscorefonts-installer_3.8.2_all.deb
   ```

## Licensing

The packaging scripts and Debian metadata are provided under their respective open-source licenses. 
**The Microsoft font files themselves are NOT included in this repository and must not be redistributed if you do not have the rights to do so.** You are responsible for acquiring legally licensed copies of the fonts for your own use.
