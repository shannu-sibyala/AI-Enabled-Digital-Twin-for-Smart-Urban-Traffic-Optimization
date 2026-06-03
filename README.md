[TrafficTwin_README.md](https://github.com/user-attachments/files/28557228/TrafficTwin_README.md)
# 🚦 TrafficTwin — AI-Enabled Digital Twin for Smart Urban Traffic Management

> **Bengaluru Pilot | Silk Board Junction**  
> An AI-powered digital twin that simulates, predicts, and optimizes real-world urban traffic — before changes are made on the ground.

---

## 📌 Overview

TrafficTwin creates a **virtual replica (digital twin)** of Bengaluru's traffic ecosystem using real-time data from Google Maps, AI-driven congestion prediction, and physics-accurate traffic simulation via SUMO.

The goal: shift traffic management from **reactive → proactive**.  
Instead of fixing jams after they happen, city planners and engineers can simulate infrastructure changes, test signal timings, and forecast congestion — all in a dashboard, without touching a single road.

> 🏆 **Recognized and funded by the Institution of Engineers India (IEI)** — approved ₹3,000 seed grant for development.

---

## 🎯 Key Features

| Feature | Description |
|--------|-------------|
| 🗺️ **Live Traffic Map** | Real-time Bengaluru traffic via Google Maps with congestion heatmap overlay |
| 🤖 **AI Congestion Prediction** | LSTM model predicts congestion hotspots 30 minutes ahead |
| 🔁 **What-If Simulation** | Adjust signal timings, close roads, toggle peak hours — see impact instantly |
| 📊 **Before vs After Metrics** | Travel time, average speed, and congestion % comparison |
| 🧠 **Digital Twin Engine** | SUMO-powered simulation synced with real road network via OpenStreetMap |
| 💻 **Interactive Dashboard** | Built with Streamlit — no-install, browser-based UI |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Road Network | OpenStreetMap + SUMO `netconvert` |
| Traffic Simulation | [SUMO](https://sumo.dlr.de/) + TraCI (Python control interface) |
| AI / ML Model | Python + TensorFlow LSTM (time-series forecasting) |
| Real Traffic Data | Google Maps Routes API |
| Map Display | Google Maps JavaScript API + Leaflet.js |
| Dashboard | Streamlit + Folium / Kepler.gl |
| Backend API | Flask / FastAPI |
| Data Storage | SQLite |
| Model Training | Kaggle Notebooks (free GPU) |
| Deployment | Render.com (free tier) |
| Prototype UI | HTML + CSS + Leaflet.js (`traffictwin3.html`) |

---

## 🧩 How It Works

```
Real World (Google Maps API)
        │
        ▼
  Data Pipeline (Python)       ──►  SQLite Database
        │                                  │
        ▼                                  ▼
  LSTM Model Training               SUMO Simulation
  (Kaggle Notebooks)                (Silk Board OSM)
        │                                  │
        └──────────────┬───────────────────┘
                       ▼
              What-If Engine (TraCI)
              Baseline vs Scenario
                       │
                       ▼
            Streamlit Dashboard
         (Google Maps + Heatmap + Metrics)
```

### What-If Simulation Flow:
1. User adjusts a parameter (e.g., signal green time, road closure)
2. Python backend applies it to SUMO via TraCI
3. Two simulations run: **Baseline** vs **Modified Scenario**
4. Results compared: travel time ↓, speed ↑, congestion % ↓
5. Difference visualized as heatmap overlay on Google Maps frontend

---

## 🤖 AI Model — LSTM Congestion Predictor

- **Model:** Long Short-Term Memory (LSTM) neural network
- **Input features:** Vehicle speed, volume, time of day, day of week, (optional) weather
- **Output:** Predicted congestion level for next **30 minutes**
- **Data source:** Google Maps Routes API — fetched every 15 minutes, stored in SQLite
- **Training:** Kaggle Notebooks (free 30hr/week GPU)

---

## 🖥️ Prototype

A working HTML prototype (`traffictwin3.html`) is included in this repo.  
It demonstrates the full dashboard UI including:
- Live map with simulated traffic heatmap (Leaflet.js)
- What-if control panel (signal sliders, road closure toggles)
- Metric cards (travel time, speed, emissions, congestion %)
- AI prediction panel
- Dark / Light mode toggle

> Open `traffictwin3.html` directly in any browser — no server required.

---

## 📁 Project Structure

```
traffictwin/
├── prototype/
│   └── traffictwin3.html        # Working UI prototype (open in browser)
├── data/
│   └── fetch_traffic.py         # Google Maps API data collector (runs every 15 min)
├── model/
│   └── lstm_model.py            # LSTM training and prediction script
├── simulation/
│   └── sumo_engine.py           # SUMO + TraCI what-if simulation engine
├── backend/
│   └── app.py                   # Flask/FastAPI backend
├── dashboard/
│   └── streamlit_app.py         # Streamlit dashboard UI
├── data/
│   └── traffic_data.sqlite      # Collected traffic data (auto-generated)
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install sumo tensorflow pandas numpy flask streamlit folium
```
Also install [SUMO](https://sumo.dlr.de/docs/Installing/index.html) and get a [Google Maps API key](https://developers.google.com/maps).

### Run the Prototype (No Setup Needed)
```bash
# Just open in browser
open prototype/traffictwin3.html
```

### Run the Full Dashboard
```bash
# Start data collection (run passively in background)
python data/fetch_traffic.py

# Start backend
python backend/app.py

# Launch dashboard
streamlit run dashboard/streamlit_app.py
```

---

## 📅 Development Timeline

| Phase | Weeks | Tasks |
|-------|-------|-------|
| Setup & Data | 1–2 | SUMO install, Google Maps API, OSM map, data collection |
| Data Pipeline | 3–4 | Routes API → SQLite, SUMO road network for Silk Board |
| AI Model | 5–6 | Train LSTM on Kaggle, validate congestion prediction |
| What-If Engine | 7–8 | TraCI integration, baseline vs scenario comparison |
| Dashboard | 9–10 | Streamlit UI, Google Maps iframe, metric cards |
| Deploy & Polish | 11–12 | Render.com deploy, cache baseline, demo prep |

---

## 🏅 Recognition

- ✅ **IEI (Institution of Engineers India)** — Project idea evaluated and approved
- ✅ **₹3,000 seed funding** granted for prototype development
- ✅ Prototype UI (`traffictwin3.html`) completed and demonstrated

---

## 📄 License

This project is developed for academic purposes as a final year major project at RNS Institute of Technology, Bengaluru.

---

*For queries, reach out via [LinkedIn](https://www.linkedin.com/in/shanmukha-manikanta/)*
