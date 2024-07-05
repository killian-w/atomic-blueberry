<div align="center">
  <img src="./resources/banner.png" alt="Atomic Blueberry"/>
</div>

<div align="center">
  <img src="https://github.com/Krosseye/atomic-blueberry/actions/workflows/build-amd-intel.yml/badge.svg" alt="Build Atomic Blueberry AMD-Intel"/>
  &nbsp;&nbsp;&nbsp;
  <img src="https://github.com/Krosseye/atomic-blueberry/actions/workflows/build-nvidia.yml/badge.svg" alt="Build Atomic Blueberry NVIDIA"/>
</div>

## About

> [!WARNING]  
>Atomic Blueberry is in an experimental phase, **everything** is subject to change. **It is not intended for everday use.**

Atomic Blueberry is an [OCI](https://en.wikipedia.org/wiki/Open_Container_Initiative) image that is optimized for both battlestations and workstations, built from [Universal Blue](https://universal-blue.org/) using [native container](https://fedoraproject.org/wiki/Changes/OstreeNativeContainerStable) workflows powered by [Fedora Atomic](https://fedoraproject.org/atomic-desktops/) technology.

Atomic Blueberry follows a hybrid release model. This means there's always a single, current version. When the underlying Fedora Kinoite releases a major update, Atomic Blueberry receives it too, after ensuring no regressions. With bi-weekly system updates and [Flatpak](https://flathub.org/) usage, packages are always kept up-to-date.

### Features

- **[v4l2loopback](https://github.com/umlaeute/v4l2loopback):** allows you to create "virtual video devices"

- **[evdi](https://github.com/DisplayLink/evdi):** kernel module required for use of displaylink

- **[xpadneo](https://github.com/atar-axis/xpadneo):** xbox one controller bluetooth driver

- **[xone](https://github.com/BoukeHaarsma23/xonedo/):** xbox one controller USB wired/RF driver modified to work along-side xpad

- **[steam-devices](https://github.com/ValveSoftware/steam-devices):** udev rules for various Steam-related hardware devices

- **[ibus-typing-booster](https://mike-fabian.github.io/ibus-typing-booster/):** a completion input method to speedup typing

### Applications

- **[OBS Studio](https://flathub.org/apps/com.obsproject.Studio):** for video capturing, recording, and live streaming

- **[Bottles](https://flathub.org/apps/com.usebottles.bottles):** run Windows software on Linux

- **[ONLYOFFICE](https://flathub.org/apps/org.onlyoffice.desktopeditors):** create, view and edit text documents, spreadsheets and presentations

- **[Kdenlive](https://flathub.org/apps/org.kde.kdenlive):** video editing application with support for many audio and video formats and advanced editing features

- **Development:**

  - **[VS Code](https://flathub.org/apps/com.visualstudio.code):** a lightweight but powerful source code editor

  - **[Distrobox](https://distrobox.it/):** use any Linux distribution inside your terminal

  - **[BoxBuddy](https://flathub.org/apps/io.github.dvlv.boxbuddyrs):** a graphical user interface for Distrobox

  - **[Boxes](https://flathub.org/apps/org.gnome.Boxes):**  select an operating system and let Boxes download and install it for you in a virtual machine

- **Gaming:**

  - **[Steam](https://flathub.org/apps/com.valvesoftware.Steam):** launcher for the Steam software distribution service

  - **[ProtonUp-Qt](https://flathub.org/apps/net.davidotek.pupgui2):** install Wine and Proton based compatibility tools

  - **[Protontricks](https://flathub.org/apps/com.github.Matoking.protontricks):** run Winetricks commands for Steam Play/Proton games among other common Wine features

  - **[Heroic Games Launcher](https://flathub.org/apps/com.heroicgameslauncher.hgl):** Epic Games, GOG and Amazon Prime games launcher

## Installation Options

> [!IMPORTANT]  
> AMD and Intel users should use `ghcr.io/krosseye/atomic-blueberry`, and Nvidia users should use `ghcr.io/krosseye/atomic-blueberry-nvidia`

### Rebase

> [!WARNING]  
> **[This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.**

To rebase an existing atomic Fedora installation to the latest build of Atomic Blueberry:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:

  ```bash
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/krosseye/atomic-blueberry:latest
  ```

- Reboot to complete the rebase:

  ```bash
  systemctl reboot
  ```

- Then rebase to the signed image, like so:

  ```bash
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/krosseye/atomic-blueberry:latest
  ```

- Reboot again to complete the installation

  ```bash
  systemctl reboot
  ```

### ISO

> [!IMPORTANT]  
> **Pre-built ISOs are currently not available, this is planned for the future.**

If built on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso).

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/krosseye/atomic-blueberry
```
