# AguaAlerta Guayaquil 🌧️

Interactive, mobile-first web prototype for the **"Intense Rains in Guayaquil"** challenge. It combines citizen participation and real-time data to help the city anticipate and respond better to flooding.

> **Status:** demo prototype. All data is simulated; there is no backend or real APIs.

---

## The problem

Every rainy season, thousands of people in Guayaquil get stuck on flooded streets without up-to-date information. Official alerts arrive late and do not show which streets are actually impassable right now.

## The solution

AguaAlerta turns every citizen into a sensor. People report the water level, the community confirms or disputes it, and the app suggests routes that avoid critical areas. An emergency assistant provides safety steps instantly.

---

## Features

| Module | Description |
|---|---|
| **Interactive map** | Map of Guayaquil built with Leaflet, with flood pins classified by severity (curb, knee, tire-covering). |
| **Report a flood** | Modal with a water-level slider, animated gauge, simulated photo upload, and submit. The new pin appears on the map with an animation. |
| **Community interaction** | Tapping a pin shows the report time, the number of confirmations, and the buttons **I confirm the flood** and **The water has receded**. |
| **Safe route** | Draws a route that avoids flooded areas and shows the estimated time. It can be toggled on and off. |
| **Emergency assistant** | Simulated chat with quick replies ("Water is entering my house", "My car stalled in the water", "Can I cross this street?") and a button to call 911. |

---

## Project structure

```
aguaalerta/
├── index.html              # Page structure
├── css/
│   ├── base.css            # Variables, reset, toast, and accessibility
│   ├── interfaz.css        # Top bar, alert, legend, and floating buttons
│   ├── pines.css           # Map pins and popups
│   ├── modal-reporte.css   # "Report a flood" modal
│   └── chat.css            # Chatbot
└── js/
    ├── config.js           # Utilities and water levels
    ├── data.js             # Initial simulated reports
    ├── toast.js            # Brief notifications
    ├── map.js              # Leaflet map and user location
    ├── reports.js          # Pins, popups, and votes
    ├── route.js            # Simulated safe route
    ├── report-modal.js     # Report modal
    └── chat.js             # Emergency chatbot
```

> Scripts are loaded in this order from `index.html`; each file uses what is defined in the previous ones. Classic scripts (not ES modules) are used so the project works with a double click, without a server.

---

## How to run it

No installation or build step required.

1. Download the entire project folder (keep the folder structure).
2. Open `index.html` by double-clicking it in Chrome, Edge, or Firefox.
3. To view it as a phone: `F12` → `Ctrl + Shift + M` → choose *iPhone 14 Pro*.

**An internet connection is required** to load the map tiles, Leaflet, and Google Fonts.

### Try it on a real phone

```bash
# From the project folder
python3 -m http.server 8000
```

Then open `http://<your-computer-IP>:8000/index.html` on the phone (both devices must be on the same Wi-Fi network).

---

## Technologies

- **HTML5 + CSS3** (no frameworks)
- **Vanilla JavaScript**
- **[Leaflet 1.9.4](https://leafletjs.com/)** for the map
- **CARTO / OpenStreetMap** as map tiles
- **Google Fonts:** Bricolage Grotesque and Figtree

---

## Prototype limitations

- Reports, votes, and the route are not saved; when the page is reloaded, everything returns to its initial state.
- The safe route is a predefined line, not a real calculation.
- The chatbot uses fixed responses, with no real AI.
- The user's location is fixed (north Guayaquil).

## Next steps

- Real-time database to store and sync reports.
- Integration with weather data (INAMHI, city weather stations).
- Real route calculation with a routing engine (OSRM, Google Maps).
- Chatbot powered by a language model and official emergency protocols.
- Report validation (user reputation and duplicate detection).
- Push notifications by zone.
- Dashboard for the city government with a heat map of critical areas.
