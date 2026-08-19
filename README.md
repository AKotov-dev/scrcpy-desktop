# scrcpy-desktop

**scrcpy-desktop** is a portable desktop integration packages (RPM/DEB) for
[scrcpy](https://github.com/Genymobile/scrcpy) on Linux.

It packages the official upstream `scrcpy` Linux binaries together
with a desktop entry and icon, providing a simple way to launch
scrcpy from the application menu.

No compilation is performed — the upstream portable binaries are
used as provided.

## Features

- Portable upstream `scrcpy` binaries
- Desktop menu entry
- Application icon
- Includes the required `scrcpy-server`
- Includes `adb` supplied with the upstream portable release
- No external runtime dependencies on FFmpeg, SDL or libusb
- Works with both X11 and Wayland
- Tested with KDE Plasma X11 and Wayland on Mageia 10
- Mouse and keyboard input tested with Android TV / Kodi

## How it works

`scrcpy-desktop` does not configure or discover Android devices.

For device discovery and ADB connection, use
[ADBManager](https://github.com/AKotov-dev/adbmanager).

Once the device is connected through ADBManager, simply launch
**ScrCpy (Android Desktop)** from the application menu.

```text
ADBManager
    │
    │  device discovery / ADB connection
    ▼
ADB server
    │
    ▼
scrcpy-desktop
    │
    ▼
Android device
```
This separation is intentional: **ADBManager** handles the potentially
complicated ADB setup, while scrcpy-desktop provides the desktop
display and control interface.

The package installs scrcpy under:
```
/opt/scrcpy/
```
and adds the `ScrCpy (Android Desktop)` application to the desktop menu.

### Usage
1. Start ADBManager.
2. Discover and connect to the Android device.
3. Launch ScrCpy (Android Desktop) from the application menu.
4. The Android screen will appear in a desktop window.

No adb connect command is required when the device has already been connected by `ADBManager`.

### X11 / Wayland
`scrcpy` works with both X11 and Wayland.

The package has been tested on:

- Mageia 10
- KDE Plasma X11
- KDE Plasma Wayland

Screen display, mouse input and keyboard input work correctly in both sessions.

If native Wayland operation is required, scrcpy also supports the
SDL Wayland backend:
```
SDL_VIDEODRIVER=wayland /opt/scrcpy/scrcpy
```
In normal use no additional configuration should be necessary.

### Upstream

This project does **not** modify `scrcpy` itself.

`scrcpy-desktop` packages the official upstream Linux portable release and adds desktop integration for Linux.

Original project: https://github.com/Genymobile/scrcpy

Please refer to the upstream project for scrcpy documentation, licensing and source code.

### Related project
**ADBManager**

ADBManager provides Android device discovery and ADB connection,
including network discovery and first-time ADB authorization.

https://github.com/AKotov-dev/adbmanager

### License

See the upstream scrcpy project for the license of the included
`scrcpy` components.

The desktop integration and packaging files in this repository are provided under the terms specified in this repository.
