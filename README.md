# ⚡ ATMOS · AI Weather Intelligence

A single-page, sci-fi-styled live weather dashboard that pulls real-time temperature, humidity, and air quality data from a ThingSpeak channel (fed by an ESP32 sensor) and renders it through a rich set of animated visualizations, charts, and effects — all in one self-contained HTML file.

![HTML5](https://img.shields.io/badge/HTML-5-orange)
![CSS3](https://img.shields.io/badge/CSS-3-blue)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-yellow)
![Chart.js](https://img.shields.io/badge/Chart.js-Canvas-red)

## ✨ Features

### Live Data
- 📡 Polls a **ThingSpeak** channel every 15 seconds for temperature, humidity, and AQI
- 📈 Live-updating **line/bar charts** (Chart.js) for temperature and humidity history
- 📊 Rolling **sparklines**, min/max tracking, trend arrows, and rate-of-change readouts
- 🧠 Rule-based **"AI" forecast engine** with a typed-out prediction and confidence bar
- 🔮 Simulated **3-day forecast** cards with icons, rain probability, and hi/lo ranges

### Visual Effects
- 🎨 Custom cursor, click ripples, 3D card tilt, glassmorphism panels
- ☀️ Real-time **sun/moon position system** based on the actual time of day
- 🌌 **Aurora borealis** effect that intensifies in cold conditions
- 🔥 **Fire particles** above 38°C, ❄️ **snowfall** below 20°C
- 🌆 Procedurally generated **neon city skyline** with flickering windows
- 🌡️ Animated canvas **thermometer** and **liquid humidity bottle**
- 🕐 24-hour **circular heat map clock**
- 🧬 Animated **neural network** visualizer and live **sensor waveform**
- 🎉 Confetti bursts, Konami code easter egg, auto-rotating color themes every 10s

### Alerts & Feedback
- ⚠️ Heat/cold/humidity threshold **alert banner**
- 🔊 Optional **voice announcements** (Web Speech API) of conditions
- 📓 Auto-generated **weather diary** log of notable readings
- 🩺 Basic **sensor health** check (detects frozen/offline sensor)
- 🔔 Audio beeps on hover/alerts (Web Audio API)

## 🛠️ Tech Stack

- **HTML5 / CSS3** — layout, glassmorphism, custom animations (no CSS framework)
- **Vanilla JavaScript** — all logic, canvas drawing, and DOM updates
- **[Chart.js](https://www.chartjs.org/)** (via CDN) — temperature/humidity charts
- **Canvas API** — nearly all custom visualizations (radar, thermometer, bottle, city, fire, snow, aurora, neural net, waveform, heatmap)
- **Web Speech API** — voice announcements
- **Web Audio API** — UI sound effects
- **[ThingSpeak](https://thingspeak.com/)** — IoT data backend (expects an ESP32 or similar publishing `field1` = temp, `field2` = humidity, `field3` = AQI)
- **Google Fonts** — Share Tech Mono, Exo 2, Michroma

## 🚀 Getting Started

No build tools or installation required.

1. Clone or download this repository.
2. Open `index.html` directly in a modern browser (Chrome/Edge recommended for full Web Speech/Audio support).
3. Data will start streaming automatically from the configured ThingSpeak channel.

### Using Your Own Sensor Data

The dashboard is hardcoded to a specific ThingSpeak channel and API key:

```js
const CHANNEL_ID = '3391744';
const API_URL = `https://api.thingspeak.com/channels/3391744/feeds.json?api_key=PDY185HIV3KX8AN2&results=20`;
```

To connect your own device:
1. Create a ThingSpeak channel with at least 3 fields: `field1` (temperature °C), `field2` (humidity %), `field3` (AQI).
2. Replace `CHANNEL_ID` and the `api_key` in `API_URL` with your own channel's values.
3. Publish readings from your ESP32/Arduino/sensor to that channel.

## 📂 Project Structure

```
atmos/
└── index.html   # All HTML, CSS, and JavaScript in a single file
```

## ⚠️ Notes & Limitations

- **Hardcoded credentials**: the ThingSpeak channel ID and API key are embedded directly in client-side JavaScript, visible to anyone viewing the page source. Don't use a private/sensitive channel here — swap in your own public read key.
- The **AI forecast** and **3-day forecast** are rule-based/pseudo-randomized (seeded by date), not powered by a real machine learning model or external weather API.
- No backend — all logic runs client-side in the browser; refreshing the page resets session min/max, streaks, and diary history.
- Designed and tested primarily for **desktop browsers**; some effects (custom cursor, hover tilt) are less meaningful on touch devices.
- Voice announcements depend on browser support for the Web Speech API and may not work in all environments (e.g. some mobile browsers).

## 🔮 Possible Improvements

- Move the ThingSpeak API key to a backend/proxy instead of client-side code
- Replace the rule-based forecast with a real weather API (e.g. OpenWeatherMap) or a trained model
- Persist history (diary, min/max, streaks) using `localStorage` or a backend database
- Add configuration UI for channel ID/API key instead of hardcoding
- Improve mobile/touch support for interactive elements

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
