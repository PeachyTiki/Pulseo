# 💪 Pulseo — All-in-One Fitness Tracker

**A single-file fitness app** that tracks habits, workouts, nutrition, and body stats — all offline, all private, zero accounts.

> Built by [PeachyTiki](https://github.com/PeachyTiki) (Monteo Pietsch)

---

## ✨ Features

- **🎯 Habit Tracker** — Yes/No and countable habits with streaks, sub-habits, drag-to-reorder, color picker
- **🏋️ Workout Planner** — 5-day split builder with live workout mode, set/exercise timers, weight logging
- **🍎 Nutrition Logger** — 580+ food database (incl. German & NZ items), macro tracking, smart serving sizes, editable meals with time tracking
- **📊 Body Stats** — Weight, body fat, progress photos, BMI calculator, line graphs
- **🐕 Easter Egg** — Find all 5 hidden dogs to unlock Muscle Dog
- **🌙 4 Visual Modes** — Dark, Light, Retro Dark (Vista blue), Retro Light (classic Windows)
- **🌍 11 Languages** — EN, ES, FR, DE, RU, ZH, JA, HI, PT, AR, BN
- **📱 Works Offline** — All data stored in localStorage, no server needed
- **🔄 Backup & Restore** — JSON export/import, AI-friendly data export for ChatGPT analysis

## 📸 Screenshots

<!-- Add your screenshots here -->
<!-- ![Dark Mode](screenshots/dark.png) -->
<!-- ![Retro Mode](screenshots/retro.png) -->

## 🚀 Quick Start

### Option 1 — Open in Browser (Easiest)
1. Download or clone this repo
2. Open `index.html` in any browser
3. That's it — everything runs locally

### Option 2 — Install on iPhone (PWA)
1. Open `index.html` in **Safari** (must be Safari)
2. Tap the **Share** button (⬆️)
3. Tap **"Add to Home Screen"**
4. Opens fullscreen like a native app

### Option 3 — Install on Android (APK)
1. Go to [WebIntoApp.com](https://webintoapp.com)
2. Upload the `apk/Pulseo.zip` file
3. Settings: Enable localStorage ✓ / Disable Pull to Refresh ✓
4. Build and install the APK

### Option 4 — GitHub Pages (Live URL)
If this repo has GitHub Pages enabled, the app is live at:
```
https://YOUR_USERNAME.github.io/Pulseo/
```

## 📂 Project Structure

```
Pulseo/
├── index.html              # The entire app (single file)
├── pulseo-clean.json       # Empty backup template (for fresh start)
├── apk/
│   └── Pulseo.zip          # Ready for WebIntoApp APK builder
├── PULSEO-HANDOFF.md       # Developer documentation
├── README.md               # You're reading this
├── LICENSE                  # MIT License
└── .gitignore
```

## 🔧 For Developers

The app is a **single HTML file** (~595KB) containing all CSS, HTML, and JavaScript inline. No build tools, no dependencies, no npm.

See [PULSEO-HANDOFF.md](PULSEO-HANDOFF.md) for:
- Full architecture overview
- All localStorage keys and data formats
- 80+ function reference
- Backup format (v7)
- Exercise, food, and habit data schemas
- Muscle Dog easter egg details

### Data Format

Backup/restore uses JSON v7 format. Workouts, habits, meals, body stats, and settings are all stored in localStorage with the `g_` prefix.

### AI Export

Settings → Export for AI generates a text file you can paste into ChatGPT for personalized workout/nutrition analysis. Includes your profile, goals, TDEE, habits, workouts, body stats, and meal history.

## 🛠 Tech Stack

- **Frontend:** Vanilla HTML/CSS/JS (no frameworks)
- **Storage:** localStorage
- **Charts:** Inline SVG (no chart library)
- **Icons:** Unicode emoji
- **Fonts:** System UI stack

## 📋 Backup Your Data

Settings → Backup → saves a `.json` file with everything. Restore it anytime on any device.

## 📄 License

MIT License — see [LICENSE](LICENSE) file.

---

**⭐ Star this repo if Pulseo helps your fitness journey!**
