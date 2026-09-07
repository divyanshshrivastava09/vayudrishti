# VayuDrishti AI

> **Environmental Intelligence. From Detection to Decision.**

VayuDrishti AI is an environmental intelligence command center designed for monitoring, analyzing, and acting upon urban air pollution. It combines real-time air quality metrics, statistical source apportionment heuristics, multi-factor environmental risk scoring, route-based exposure reduction models, and policy intervention simulations into a futuristic dark HUD interface.

---

## 🌟 Key Capabilities & Features

1. **Air Quality Telemetry Monitoring**: Live/DEMO monitoring of AQI, fine particulate (PM2.5), coarse particulate (PM10), and AQI severity brackets.
2. **City Switching & Custom Geo-Coordinates**: Instant preset navigation across major Indian urban centers (Vijay Nagar/Indore, Anand Vihar/Delhi, BKC/Mumbai, Victoria Memorial/Kolkata, HITEC City/Hyderabad, BTM Layout/Bengaluru, Pan Bazaar/Guwahati) or custom latitude/longitude coordinate input.
3. **Geospatial Pollution Radar & Hotspot Radial**: Interactive Google Maps JavaScript API integration (with tilt, heading, markers, and circular heat zones) with an automatic fallback to an HTML5 Canvas-based tactical radar HUD when external APIs are offline.
4. **Pollution Source Apportionment Investigation**: AI aerosol ratio diagnostic estimation attributing particulate load between **Traffic (72%)**, **Industrial Activity (18%)**, and **Open Biomass Burning (10%)** (clearly labeled as `AI ESTIMATE`).
5. **Operational Environmental Risk Scoring**: Multi-factor risk engine computing numerical scores (0–100) and advisory classifications (`LOW`, `MODERATE`, `HIGH`, `CRITICAL`).
6. **Commute Route Exposure Comparison**: Compares a direct arterial corridor against a lower-exposure eco-bypass corridor with calculated particulate inhalation reduction (e.g., **37.8% lower estimated exposure**).
7. **Policy Intervention Simulator**: Interactive sliders for Traffic Reduction, Industrial Emission Caps, and Open Burning Bans with immediate projected AQI calculations (clearly labeled as `SIMULATION`).
8. **Vertex AI / Gemini Environmental Assistant**: Context-aware natural language assistant answering queries on localized AQI causes, route exposure, and intervention priorities with built-in text-to-speech (TTS) accessibility.
9. **Atmospheric Dispersion Trend Radar**: 24-hour visual trend canvas illustrating diurnal particulate flux.
10. **Robust Fallback Engine (Zero Crash Guarantee)**: The platform operates continuously in **DEMO MODE** if Google Maps, Google Air Quality, Google Routes, Vertex AI, or the Python backend are unavailable.

---

## 🏗️ Architecture

```
                                USER
                                  |
                                  v
                HTML5 + CSS3 + Vanilla JavaScript
                    (HUD Glassmorphism Dashboard)
                                  |
                                  v
                          Node.js + Express
                         (API Gateway Server)
                                  |
            +---------------------+---------------------+
            |                     |                     |
            v                     v                     v
    Google Maps JS API    Google Air Quality API    Vertex AI / Gemini
    (Live Map & Routes)   (Live Pollutants)         (GenAI Assistant)
            |                     |
            +----------+----------+
                       |
                       v
                 Python FastAPI
             (Intelligence Service)
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
   Risk Engine   Pollution AI   Route Exposure
        |
        v
Intervention Engine
        |
        v
Future ML Models
```

---

## 📁 Project Directory Structure

```
aerotrace-ai/
│
├── package.json               # Node.js dependencies & scripts
├── .env                       # Local environment variables
├── .env.example               # Environment template
├── .gitignore                 # Git ignore configuration
├── server.js                  # Express API Gateway server & fallbacks
├── README.md                  # Complete platform documentation
│
├── public/                    # Frontend Client
│   ├── index.html             # Semantic HUD Single-Page Application
│   ├── style.css              # Cyber-environmental dark glassmorphism theme
│   └── app.js                 # Vanilla JS state, map engine, charts, & API client
│
├── python/                    # Python Intelligence & Analytics Service
│   ├── requirements.txt       # FastAPI, Uvicorn, Pydantic, Dotenv
│   ├── main.py                # FastAPI application entrypoint
│   │
│   ├── services/              # Analytics & Simulation Modules
│   │   ├── __init__.py
│   │   ├── air_quality.py     # Metric normalization & brackets
│   │   ├── pollution_analysis.py # Heuristic source apportionment
│   │   ├── risk_engine.py     # Multi-factor environmental risk model
│   │   ├── route_exposure.py  # Arterial vs eco-bypass exposure model
│   │   └── intervention.py    # Policy scenario simulation engine
│   │
│   └── models/                # ML Model Checkpoints & Architecture
│       └── __init__.py
│
├── data/                      # Environmental Datasets
│   ├── raw/
│   │   └── README.md
│   ├── processed/
│   │   └── README.md
│   └── metadata/
│       └── stations.json      # Verified monitoring station records
│
├── models/                    # ML Registry
│   └── README.md              # Future forecasting & anomaly models roadmap
│
└── reports/                   # Generated Reporting Artifacts
    └── .gitkeep
```

---

## ⚡ Quick Start & Setup

### Prerequisites
- **Node.js** (v18.0 or newer)
- **Python** (v3.9 or newer)

---

### Step 1: Start the Python Intelligence Service (Optional for Demo Mode)

In a PowerShell or terminal window:

```powershell
cd c:\Users\Riya\Downloads\Vayudrishti\python
python -m venv venv
.\venv\Scripts\activate
pip install -r requirements.txt
python main.py
```

*The Python FastAPI service will run on `http://127.0.0.1:8000`.*

---

### Step 2: Start the Node.js API Gateway

In a second PowerShell or terminal window:

```powershell
cd c:\Users\Riya\Downloads\Vayudrishti
npm start
```

*The Node Gateway will start on `http://localhost:8080`.*

---

### Step 3: Open the Command Center

Open your browser and navigate to:

👉 **`http://localhost:8080`**

---

## 🔑 Environment Variables Configuration

To connect live Google Services and Vertex AI, update your `.env` file:

```env
PORT=8080
PYTHON_API_URL=http://127.0.0.1:8000

# Optional: Google Maps & Air Quality API Key
GOOGLE_MAPS_API_KEY=

# Optional: Google Cloud Project for Vertex AI
GOOGLE_PROJECT_ID=
GOOGLE_LOCATION=us-central1

# Optional: Gemini API Key for Direct Assistant Access
GEMINI_API_KEY=
```

> **Note**: If API keys are omitted or external services fail, AEROTRACE AI automatically switches to its deterministic **DEMO MODE** fallback, ensuring a seamless hackathon presentation.

---

## 📡 API Endpoint Reference

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/health` | Node Gateway health and uptime check |
| `GET` | `/api/config` | Client-safe configuration (Maps Key flag) |
| `GET` | `/api/python-health` | Python FastAPI intelligence service status |
| `GET` | `/api/air-quality?lat=..&lng=..` | Current AQI, PM2.5, PM10 metrics |
| `POST` | `/api/investigate` | Source apportionment analysis (`AI ESTIMATE`) |
| `POST` | `/api/risk` | Environmental risk score & advisory |
| `POST` | `/api/route` | Direct vs lower-exposure route calculation |
| `POST` | `/api/intervention` | Policy intervention simulation (`SIMULATION`) |
| `POST` | `/api/chat` | AI Environmental Assistant (Gemini / Knowledge Base) |

---

## 🛡️ Hackathon Demonstration Integrity

- **LIVE vs DEMO Distinction**: Fallback datasets are explicitly tagged with `DATA: DEMO` and `DEMO RADAR HUD` indicators. Live data from Google APIs is tagged `DATA: LIVE`.
- **Classification Transparency**: Source apportionment outputs are labeled `AI ESTIMATE`, and policy projections are tagged `SIMULATION`.
- **Operational Risk Standard**: Risk scores are clearly defined as computational operational intelligence metrics rather than statutory medical diagnoses.
