# i2pd-meson-build

Experimental Meson build system support for i2pd 

## What you need

Basically the same dependencies as the classic build, just check the official docs too:  
https://docs.i2pd.website/en/latest/devs/building/requirements/

- C++17-capable compiler  
  (MSVC 2019+, GCC 9+, Clang 10+)  
  **-> GCC 14 is currently the safest choice with this meson setup**

- Boost ≥ 1.66  
- OpenSSL ≥ 1.1.1   **or**   LibreSSL ≥ 4.0  
- zlib

## Quick setup

### Windows (MSYS2 UCRT64)

```bash
pacman -Syu
```

```bash
pacman -S \
  mingw-w64-ucrt-x86_64-gcc \
  mingw-w64-ucrt-x86_64-meson \
  mingw-w64-ucrt-x86_64-ninja \
  mingw-w64-ucrt-x86_64-boost \
  mingw-w64-ucrt-x86_64-openssl \
  mingw-w64-ucrt-x86_64-zlib \
  mingw-w64-ucrt-x86_64-git \
  python
```

### Debian / Ubuntu

```bash
sudo apt update
sudo apt install -y \
  meson ninja-build pkg-config \
  g++ git python3 \
  libboost-all-dev libssl-dev zlib1g-dev
```

## To build

### Get the sources

```bash
git clone https://github.com/PurpleI2P/i2pd.git
cd i2pd
```

### Add the meson.build file

Copy the `meson.build` from this repo and place it directly in the root of the i2pd folder

### Build (pick one)

**Debug build** (debug mode – default)

```bash
meson setup build-debug
meson compile -C build-debug
```

**Release build** (recommended for normal usage – faster & smaller)

```bash
meson setup build-release --buildtype=release
meson compile -C build-release
```

The resulting binary will be:

- Windows -> `build-release/i2pd.exe`  
- Debian -> `build-release/i2pd`

### To install (optional):

```bash
sudo meson install -C build-release
```

## Tested on

Works:

- Windows
- Debian

Probably works (not tasted):
- Arch/Manjaro
- Fedora/RHEL/CentOS Stream
- macOS
- FreeBSD
- OpenBSD
- Solaris/OpenIndiana

If you get it building (or failing) on something else (arch, haiku, solaris or whatever) please open an issue or just comment with what happened :)
