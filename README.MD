# 👁️ RSVP · EYEREAD

> **Speed read with your eyes — literally.**  
> A browser-based RSVP reader that uses your webcam to pause reading when you blink or close your eyes.

<!-- Replace the image below with your own screenshot -->
![RSVP EyeRead Screenshot](./screenshots/app-screenshot.png)

---

## ✨ Features

| Feature | Description |
|---|---|
| 👁️ **Eye Tracking** | Uses your webcam + face-api.js to detect blinks in real time |
| ⏸️ **Auto Pause** | Pauses the reader the moment your eyes close (>200ms) |
| 🔁 **Previous Word Recall** | Shows the last word you saw when your eyes close, so you never lose your place |
| 📈 **WPM Ramp-Up** | Smoothly accelerates from 80 WPM up to your target speed |
| 🎯 **ORP Focus Guide** | Highlights the optimal recognition point in each word for faster comprehension |
| 🖱️ **Draggable Camera** | Webcam preview is draggable and resizable — put it wherever you like |
| ⚡ **Punctuation Pauses** | Configurable extra pause time after `.`, `,`, `?`, etc. |
| 🎛️ **Sensitivity Tuning** | Dial in the eye-close sensitivity to match your blink style |

---

## 📸 Screenshots



<!-- Main app view -->
### Main Interface
![Main Interface](./screenshots/app-screenshot.png)


---

## 🚀 Getting Started

No install needed. It's a single HTML file.

### Option 1 — Open directly

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/rsvp-eyeread.git

# Open in your browser
open rsvp-reader.html
```

### Option 2 — Serve locally (recommended for camera access)

```bash
# Using Python
python3 -m http.server 8080

# Then visit
http://localhost:8080/rsvp-reader.html
```

> ⚠️ **Camera permission required.** Your browser will ask for webcam access — this is only used locally for eye tracking. No data is sent anywhere.

---

## 🎮 How to Use

1. **Paste** any text into the left panel
2. **Set** your target WPM, ramp time, and sensitivity
3. **Click START** — the model loads once, then tracking begins
4. **Read** — words flash one at a time at your target speed
5. **Blink freely** — the reader pauses whenever your eyes close for more than 200ms, shows you the last word, then ramps back up when you open your eyes

---

## 🎛️ Controls

| Control | Range | What it does |
|---|---|---|
| **Target WPM** | 100 – 900 | How fast to read at full speed |
| **Ramp Time** | 2 – 20s | How long to take accelerating to full WPM |
| **Eye Sensitivity** | 1 – 10 | How sensitive blink detection is (higher = pauses on lighter blinks) |
| **Punct. Pause** | 0 – 5× | Extra pause multiplier after punctuation |

---

## 🧠 How It Works

```
Webcam feed → face-api.js → 68-point facial landmarks
                                        ↓
                           Eye Aspect Ratio (EAR) calculated
                                        ↓
                    EAR below threshold for 200ms → PAUSE
                                        ↓
                         Shows previous word on screen
                                        ↓
                    Eyes reopen → ramp back up to target WPM
```

**Eye Aspect Ratio (EAR)** is a classic blink detection metric:

```
EAR = (‖p2 − p6‖ + ‖p3 − p5‖) / (2 × ‖p1 − p4‖)
```

When the eye closes, vertical distances shrink → EAR drops below threshold → pause triggered.

---

## 🛠️ Tech Stack

- **Vanilla HTML/CSS/JS** — zero build step, zero dependencies to install
- **[face-api.js](https://github.com/vladmandic/face-api)** — TensorFlow.js-based face & landmark detection
- **TinyFaceDetector + 68-point Landmark Model** — lightweight, runs in real time in-browser
- **[JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) + [Syne](https://fonts.google.com/specimen/Syne)** — typography

---

## 🌐 Browser Support

| Browser | Status |
|---|---|
| Chrome / Edge | ✅ Fully supported |
| Firefox | ✅ Supported |
| Safari | ⚠️ Camera may need explicit permission |
| Mobile | ❌ Not recommended (performance) |



---

## 🔒 Privacy

- All processing happens **entirely in your browser**
- Your webcam feed **never leaves your device**
- No analytics, no tracking, no servers

---

## 📄 License

MIT — do whatever you like with it.

---

<div align="center">

Made with 👁️ and too much coffee

</div>
