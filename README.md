# DevilutionX Asset Optimizer

A specialized utility suite designed to process and optimize game assets for **DevilutionX**, specifically tailored to reduce memory usage on constrained devices (such as retro consoles, mobile devices, and older hardware).

> [!IMPORTANT]
> **Not a General Extraction Tool:** This utility is designed to **convert and minify** assets into optimized formats (such as CLX) for use with DevilutionX. If you want to extract original files for the purpose of modding, please use a standard MPQ editor like `smpq` or [MPQ Editor](http://www.zezula.net/en/mpq/download.html) instead.

---

## `unpack_and_minify_mpq`

This utility unpacks an MPQ archive and transforms its contents into highly efficient formats. By converting assets, it significantly lowers the RAM overhead required by the game engine, making it ideal for platforms with limited resources.

### Key Features

* **Memory Optimization:** Specifically tuned to help DevilutionX run on memory-constrained devices.
* **CLX Conversion:** Automatically converts graphical assets to the optimized CLX format.
* **Asset Minification:** Strips unnecessary data and reduces file footprints.
* **Audio Processing (Planned):** Support for WAV to MP3 conversion via the `--mp3` flag is currently in development.

---

## Getting Started

### Installation

**Windows**

1. Download the latest binary from the [Releases Page](https://github.com/diasurgical/devilutionx-mpq-tools/releases).
2. Place the binary in the same directory as your `.mpq` files.

**Linux / macOS**
Please follow the [Build from Source](https://www.google.com/search?q=%23build-from-source) instructions below.

### Usage

Run the tool directly from your terminal or command prompt:

```bash
./unpack_and_minify_mpq

```

For advanced configuration and a full list of flags, use:

```bash
./unpack_and_minify_mpq --help

```

---

## Build from Source

Ensure you have **CMake** and **Ninja** installed on your system.

**1. Configure and Build**

```bash
cmake -S. -Bbuild-rel -G Ninja -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=OFF
cmake --build build-rel -j $(getconf _NPROCESSORS_ONLN)
```

**2. Install**

```bash
sudo cmake --install build-rel
```
