A set of scripts to build KiCad on Android using wxQt wxWidgets port.

# Requirements

- A modern Linux Distro (Ubuntu 22.04)
- Android SDK
- [Android NDK r25c](https://github.com/android/ndk/wiki/Unsupported-Downloads#r25c) (newer versions won't work)
- Android 9+ (API Level 28) Emulator or Device. xlocale support doesn't work on lower versions.
- Qt 6.6.2
- CMake

# Init repo

```bash
git submodule update --init --recursive
```

# Get tarballs

```bash
mkdir -p OCCT && curl -o - 'https://codeload.github.com/Open-Cascade-SAS/OCCT/tar.gz/refs/tags/V7_8_0' | tar -xz --strip-components=1 -C OCCT
mkdir -p libgit2 && curl -o - 'https://codeload.github.com/libgit2/libgit2/tar.gz/refs/tags/v1.8.0' | tar -xz --strip-components=1 -C libgit2
mkdir -p ngspice && curl -o - 'https://altushost-swe.dl.sourceforge.net/project/ngspice/ng-spice-rework/42/ngspice-42.tar.gz' | tar -xz --strip-components=1 -C ngspice
mkdir -p cairo && curl -o - 'https://gitlab.freedesktop.org/cairo/cairo/-/archive/1.18.0/cairo-1.18.0.tar.gz' | tar -xz --strip-components=1 -C cairo
mkdir -p unixODBC && curl -o - 'ftp://ftp.unixodbc.org/pub/unixODBC/unixODBC-2.3.12.tar.gz' | tar -xz --strip-components=1 -C unixODBC
```

# Patch GLU

```bash
cp _glu_meson.build glu/meson.build
```

# Qt installation
1. Download Qt sources (qt-everywhere-src-6.6.2)
2. Build Qt for Desktop
3. Build Qt for Android

**Tweak paths to your tooling in `init-env` file.**

# TBD

# Start build

```bash
./all.sh
```

# References

- Original proof of concept: https://github.com/reingart/gsoc2014
- Minimal wxWidgets tooling: https://github.com/dsa-t/wx-android-minimal-cmake
