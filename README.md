# 🎥 Recordino Skyroom

> **A powerful, lightweight Chrome Extension (Manifest V3) designed to record Skyroom and online classes with crystal-clear audio passthrough, microphone mixing, and seekable video export.**

[![Manifest V3](https://img.shields.io/badge/Manifest-V3-success.svg)](https://developer.chrome.com/docs/extensions/mv3/intro/)
[![Chrome Extension](https://img.shields.io/badge/Chrome-Extension-blue.svg)](https://www.google.com/chrome/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## ✨ Features

- 🔊 **Zero Audio Interruption (Audio Passthrough):** Solves Chrome's default behavior of muting the tab during capture. You can listen to your teacher/class through your speakers or headphones while recording.
- 🎤 **Microphone Mixing with Echo Cancellation:** Record your own questions and responses alongside the class audio with built-in hardware echo cancellation and noise suppression.
- ⏱️ **Seekable Video Fix:** Built-in WebM duration metadata injection ensures your exported videos have full timeline scrubbing (no infinite duration or broken seekbars in VLC/media players).
- ⚙️ **Custom Quality & Resolution Control:** Choose between **1080p (High)**, **720p (Standard)**, and **480p (Low)** with adjusted bitrates and hardware-friendly frame rates to save CPU and disk space.
- 🔄 **Manifest V3 Sleep-Proof:** State is persisted via `chrome.storage.session`, ensuring that long recordings (1 to 3+ hours) maintain timers and controls even when the background service worker goes idle.
- ⚡ **Global Shortcut:** Start or stop recording instantly with `Alt + Shift + R` without having to open the popup.
- 🛡️ **Safe Auto-Download:** Uses the official `chrome.downloads` API for reliable, uninterrupted file saves.
- 🎨 **Modern, Clean UI:** Sleek glass-styled interface with real-time pulsing indicators and tabular digital timer.

---

## 🚀 Installation (Load Unpacked)

Since this extension is built with standard web technologies and Chrome Manifest V3, you can easily install it in developer mode:

1. **Clone or Download** this repository:
   ```bash
   git clone https://github.com/cheetahcoder/recordino-skyroom.git
   ```
2. Open Google Chrome (or any Chromium-based browser like Brave, Edge, or Arc).
3. Navigate to:
   ```text
   chrome://extensions
   ```
4. Enable **Developer mode** using the toggle switch in the top-right corner.
5. Click **Load unpacked** in the top-left corner.
6. Select the folder containing `manifest.json`.
7. **Recordino Skyroom** is now installed and ready to record!

---

## 💡 How to Use

1. Open your online class or lecture tab (e.g., [Skyroom](https://www.skyroom.online/), Google Meet, Adobe Connect).
2. Click the **Recordino Skyroom** icon in the Chrome toolbar (or press `Alt + Shift + R`).
3. Configure your preferences:
   - Toggle **Microphone** on/off.
   - Choose desired **Video Quality** (1080p, 720p, or 480p).
4. Click **Start Recording**.
5. During the session, you can **Pause**, **Resume**, or finish by clicking **Stop & Save**.
6. The video file will automatically be saved to your default `Downloads` directory formatted as:
   `Recordino_Skyroom_[TabTitle]_[Date].webm`

---

## 🛠️ Architecture & Tech Stack

- **Manifest V3:** Adheres to Chrome's latest extension standard.
- **Chrome Offscreen API:** Offloads heavy MediaStream capturing and Web Audio processing into an isolated background document.
- **Web Audio API (`AudioContext`):** Routes captured tab audio to `audioCtx.destination` (speakers) and mixes microphone streams into a single multi-track destination.
- **MediaStream & MediaRecorder:** Chunks encoded video in 1-second timeslices for memory stability.
- **EBML Duration Injector (`fix-webm-duration.js`):** Patches the WebM container header before final disk output to restore seekbars.

---

## 🤝 Contributing

Contributions, bug reports, and feature suggestions are welcome! Feel free to open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
