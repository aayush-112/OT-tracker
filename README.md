# ⏱ OT Tracker

A fully offline Progressive Web App (PWA) for tracking overtime, attendance, and payslips — built specifically for Nepal with Bikram Sambat calendar support.

> Install it on your Android phone like a real app. No Play Store. No internet required after install.

---

## Screenshots

| Dashboard | OT Requests | Nepali Calendar | Payslip |
|-----------|-------------|-----------------|---------|
| Live clock in BS/AD, check-in/out, OT charts | Submit OT for approval, carryover tracking | Offline BS calendar with holidays & tithi | Auto-filled attendance, Foodmandu-style print |

---

## Features

### ⏰ Time Tracking
- One-tap check-in / check-out from the dashboard
- Manual entry with BS date preview
- Auto-calculates OT based on your shift hours
- Flags missing check-outs

### 📋 OT Requests
- Pick a day you worked OT — hours auto-filled from your log
- Submit requests with reason and notes for superior approval
- Approve with full or partial hours
- **Carryover logic** — OT worked in Magh but approved in Falgun is correctly tracked as Magh's OT

### 📅 Nepali Calendar (fully offline)
- Complete BS calendar with month navigation
- **Tithi** (lunar day) shown on every date
- Nepal public holidays for 2081 & 2082 bundled
- Upcoming holidays panel with days-away countdown
- Check-in days highlighted directly on the calendar

### 🧾 Payslips
- Matches **Foodmandu Pvt. Ltd.** payslip format exactly
- Auto-fills present days, leave, absent, OT from your check-in log
- **Attendance rules:**
  - Missed exactly 1 day in a week → auto **Holiday**
  - Missed 2+ days → notification bar lets you mark each day as **Leave** or **Absent**
- Print-ready payslip output with signature lines

### 📊 Summary
- Weekly and monthly OT charts (native Canvas, no libraries)
- BS month labels throughout
- Approved OT vs actual balance

### 🌙 Other
- Dark / light mode
- Daily **11:20 PM reminder** notification to review your log
- Export CSV and PDF
- 100% offline — all data stored in device localStorage

---

## Tech Stack

| | |
|---|---|
| **Frontend** | Vanilla HTML, CSS, JavaScript — single file |
| **Charts** | Native Canvas API (no Chart.js) |
| **Calendar** | Built-in BS conversion engine (2000–2090) |
| **Storage** | `localStorage` — stays on your device |
| **Offline** | Service Worker caches all assets |
| **Fonts** | System font stack — no Google Fonts |

No frameworks. No dependencies. No internet required.

---

## Install on Android

### Option 1 — Via GitHub Pages (recommended)

1. Fork this repo
2. Go to **Settings → Pages → Source → `main` branch → Save**
3. Wait ~1 minute, then open the generated URL in **Chrome on your Android phone**
4. Chrome will show an **"Add to Home Screen"** prompt — tap it
5. The app installs to your home screen and works fully offline ✓

### Option 2 — Self-host locally

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/ot-tracker.git
cd ot-tracker

# Serve with any static server (needs HTTPS or localhost for SW to work)
npx serve .
# or
python3 -m http.server 8000
```

Open `http://localhost:8000` in Chrome → Add to Home Screen.

> **Note:** Service Workers require either `localhost` or an `https://` URL. Plain `http://` on a network IP won't register the SW (app still works, just not offline-cached).

---

## File Structure

```
ot-tracker/
├── index.html        # The entire app (HTML + CSS + JS, single file)
├── manifest.json     # PWA manifest — makes it installable
├── sw.js             # Service Worker — enables offline use
├── icons/
│   ├── icon-192.png  # Home screen icon
│   └── icon-512.png  # Splash screen icon
└── README.md
```

---

## Data & Privacy

- All data is stored in **your browser's `localStorage`** on your device
- Nothing is sent to any server — ever
- Uninstalling the app or clearing browser data will erase your entries
- Use **Settings → Export CSV** regularly to back up your data

---

## Notification Permission

On first launch the app will ask to enable notifications. If you allow it, you'll get a daily **11:20 PM reminder** to review your OT log. The notification message is smart:

- Still checked in → *"You are still checked in! Don't forget to check out."*
- Has entries today → *"You have X entries today. Review your OT log."*
- No check-in → *"No check-in recorded today. Open the app to review."*

> The app must be open in a browser tab for the notification to fire. This is a browser limitation, not a bug.

---

## BS Calendar Data

The Bikram Sambat conversion engine covers years **2000–2090 BS** and is fully self-contained. No API calls. The following data is bundled:

- Month day counts for all BS years (2000–2090)
- Nepal public holidays for **2081 BS** and **2082 BS**
- Tithi (lunar day) calculated mathematically from lunar cycle

---

## Contributing

Pull requests welcome — especially for:
- Holiday data for additional BS years
- Multi-employee support
- OT rate multipliers (1.5×, 2× for weekends/holidays)

---

## License

MIT — free to use, modify, and distribute.

---

*Built for daily use at a Nepali office. Designed to match the Foodmandu payslip format.*
