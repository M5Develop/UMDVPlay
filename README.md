# UMDVPlay (UMD Video Player)

![License: GPL v2](https://img.shields.io/badge/License-GPLv2-blue.svg)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20Android-lightgrey)
![Status](https://img.shields.io/badge/Status-Planning-yellow)
![Language](https://img.shields.io/badge/Language-C%2B%2B17-orange)

A lightweight, cross-platform, modern C++ library and standalone media player designed to parse, decode, and play UMD Video ISOs. 

The ultimate goal of this project is to achieve a stable, low-overhead emulation layer for UMD Video playback that can be seamlessly integrated into existing PSP emulators (such as PPSSPP) or used as a standalone preservation tool.

---

## 🚀 Vision & Motivation
While PlayStation Portable (PSP) game emulation has reached near-perfection, native support for **UMD Video ISOs** remains largely unsupported or unstable across major emulators. UMD Video discs utilize a specific structure (`UMD_VIDEO` directory) containing MPEG Program Stream (`.MPS`) containers with H.264 video tracks, alongside ATRAC3plus or LPCM audio formats and interactive menu overlays.

**UMDVPlay** aims to solve this missing link in PSP preservation by building a dedicated, efficient decoder from scratch using pure C++ and FFmpeg, heavily optimized to run even on low-spec legacy hardware.

---

## 🛠️ Tech Stack & Dependencies
To ensure maximum portability and performance, the project is strictly built upon:
* **Language:** Modern C++ (C++17 standard)
* **Decoder Pipeline:** FFmpeg APIs (for H.264 AVC, ATRAC3plus, and LPCM decoding). *Note: FFmpeg will be linked via pre-compiled static libraries to ensure strict architecture control.*
* **Window & Event Management:** SDL2 (configured with a lightweight Software Renderer option to guarantee legacy hardware compatibility).
* **Build System:** CMake (for seamless cross-platform deployment).

### Target Platforms:
* 🪟 Windows (MinGW/MSVC toolchains)
* 🐧 Linux (Native GCC)
* 🤖 Android (via Android NDK — *Long-term target, contributions welcome*)

---

## 📂 Project Directory Structure
```text
UMDVPlay/
├── CMakeLists.txt             # Core build configuration
├── docs/
│   └── ARCHITECTURE.md        # Technical breakdown of the decoding pipeline
├── include/                   # Core header files (.h)
│   ├── iso_reader.h           # ISO VFS and UDF parser layout
│   ├── decoder.h              # FFmpeg context handles and demuxing
│   └── ui_manager.h           # SDL2 software rendering loop
├── src/                       # Core implementation files (.cpp)
│   ├── main.cpp               # Application entry point
│   ├── iso_reader.cpp         
│   ├── decoder.cpp            
│   └── ui_manager.cpp         
└── thirdparty/                # Vendor dependencies (Header/Library trees)
    ├── ffmpeg/
    └── sdl2/

```

---

## 🗺️ Roadmap

* [ ] **Phase 1:** Implement a robust ISO Parser to navigate the `UMD_VIDEO/STREAM/` directory and extract raw bytes.
* [ ] **Phase 2:** Integrate FFmpeg for demuxing and decoding `.MPS` containers (Strict Audio/Video Synchronization).
* [ ] **Phase 3:** Develop the standalone GUI using SDL2 with stable Play, Pause, and Seek functionalities.
* [ ] **Phase 4:** Research and reverse-engineer UMD interactive menus (`.RCO` / `.VBO` overlays).
* [ ] **Phase 5:** Expose a clean C-style API for seamless integration into PPSSPP.

---

## 🤝 Contributing

This project is open-source and highly welcoming to Reverse Engineers, Emulation Developers, and Multimedia enthusiasts.

To maintain a clean codebase, please review our planned development roadmap and architecture notes in `docs/ARCHITECTURE.md` before submitting pull requests or opening structural issues.

---

## 📜 License

This project is licensed under the **GNU General Public License v2.0 (GPLv2)** - ensuring native license compatibility and smooth upstream integration with the PPSSPP project.

*Disclaimer: This project is strictly for digital preservation and educational purposes. "PSP" and "UMD" are trademarks of Sony Interactive Entertainment Inc.*
