# UMDVPlay (UMD Video Player)

A lightweight, cross-platform, modern C++ library and standalone media player designed to parse, decode, and play UMD Video ISOs. 

The ultimate goal of this project is to achieve a stable, low-overhead emulation layer for UMD Video playback that can be seamlessly integrated into existing PSP emulators (such as PPSSPP) or used as a standalone preservation tool.

---

## 🚀 Vision & Motivation
While PlayStation Portable (PSP) game emulation has reached near-perfection, native support for **UMD Video ISOs** remains largely unsupported or unstable across major emulators. UMD Videos utilize a specific structure (`UMD_VIDEO` directory) containing multiplexed MPEG-2 Transport Streams (`.MPS`/`.PMF`) with H.264 video and ATRAC3plus/LPCM audio formats, alongside interactive menu overlays.

**UMDVPlay** aims to solve this missing link in PSP preservation by building a dedicated, efficient decoder from scratch using pure C++ and FFmpeg, optimized to run even on low-spec legacy hardware.

---

## 🛠️ Tech Stack & Architecture
To ensure maximum portability and performance, the project is strictly built upon:
* **Language:** Modern C++ (C++17 / C++20 standard)
* **Decoder Pipeline:** FFmpeg APIs (for H.264 AVC, ATRAC3plus, and LPCM decoding)
* **Window & Event Management:** SDL2 (configured with a lightweight Software Renderer option for legacy GPU compatibility)
* **Build System:** CMake (for seamless cross-platform deployment)

### Target Platforms:
* 🪟 Windows (MinGW/MSVC)
* 🐧 Linux
* 🤖 Android (via Android NDK)

---

## 📂 Planned Core Structure
```text
UMDVPlay/
├── src/                # Core C++ implementation files (.cpp)
│   ├── main.cpp        # Application entry point
│   ├── iso_reader.cpp  # UMD ISO file system parser
│   ├── decoder.cpp     # FFmpeg synchronization & decoding logic
│   └── ui_manager.cpp  # SDL2 UI and event rendering
├── include/            # Core header files (.h)
└── thirdparty/         # External dependencies (FFmpeg, SDL2)

```

---

## 🗺️ Roadmap

* [ ] **Phase 1:** Implement a robust ISO Parser to navigate the `UMD_VIDEO/STREAM/` directory and extract raw streams.
* [ ] **Phase 2:** Integrate FFmpeg for demuxing and decoding `.MPS` files (A/V Synchronization).
* [ ] **Phase 3:** Develop the standalone GUI using SDL2 with stable Play, Pause, and Seek functionalities.
* [ ] **Phase 4:** Expand to support UMD interactive menus and subtitle overlays.
* [ ] **Phase 5:** Expose a clean API for easy integration into PPSSPP.

---

## 🤝 Contributing & Support

This project is open-source and highly welcoming to Reverse Engineers, Emulation Developers, and Multimedia enthusiasts. Feel free to open issues, discuss architecture, or submit pull requests.

*Disclaimer: This project is strictly for digital preservation and educational purposes. "PSP" and "UMD" are trademarks of Sony Interactive Entertainment Inc.*
