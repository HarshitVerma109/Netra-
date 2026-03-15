# 🛡️ NETRA — Device-Level Geospatial Intelligence Platform

**NETRA** is a full-stack **Device-Level Geospatial Intelligence Platform** built for tracking and analyzing mobile devices across a defined geographic area (SMVDU Campus, Katra, J&K). It uses synthetic commercial location data to extract meaningful behavioral insights and threat detection, serving as a proof-of-concept for ADINT (Advertising Intelligence).

## 🌟 Key Features
- **GPS Tracking:** Tracks 40 simulated devices over a 30-day period.
- **Home/Work Detection:** Utilizes DBSCAN clustering to infer where device owners likely live and work.
- **Anomaly Detection:** Hybrid approach using Machine Learning (Isolation Forest) and rule-based behavior analysis (based on 7 distinct spatial-temporal features) to spot irregular movements.
- **Co-Traveler Analysis:** Employs H3 spatial indexing to identify device associations and possible coordinated threat actors.
- **Geo-Fence Monitoring:** Shapely polygon-based zone monitoring to track incursions in sensitive areas (e.g., Helipad, VC House).
- **Real-Time Alert System:** Pushes instant notifications via WebSockets.
- **Live GPS Integration:** Integrates with the OwnTracks mobile app via ngrok for real-time device tracking.
- **AI Chatbot:** Built-in RAG-based chatbot using Google Gemini 2.5 Flash API to query system intelligence intuitively.

## 🛠️ System Architecture & Tech Stack

### Data & ML Core
- Python 3.10+
- **Database / Pipelines**: DuckDB, Parquet 
- **Data Computation**: Pandas, NumPy, scikit-learn, Shapely
- **Geospatial Indexing**: Uber H3

### Backend
- **Framework:** FastAPI (REST + WebSockets)
- **Live Sync:** Uvicorn WebSocket broadcasting

### Frontend
- **Framework:** React 18 & Vite
- **UI & Mapping:** Deck.gl (WebGL map rendering for 100k+ points), MapLibre GL, react-map-gl
- **Visuals:** Recharts, Framer Motion, Lucide React

## 🚀 How to Run the Project

### Prerequisites
- Python 3.10+
- Node.js 18+

### 1. Backend Setup
```bash
cd backend
pip install -r requirements.txt

# Generate synthetic positional data (one-time)
python -m data_gen.generator

# Start the FastAPI server
python main.py
```
*Server runs on: http://localhost:8000*  
*Swagger docs available at: http://localhost:8000/docs*

### 2. Frontend Setup
```bash
cd frontend
npm install
npm run dev
```
*Dashboard runs on: http://localhost:5173*

### 3. Usage & Live Demo
- Once the dashboard is running, navigate to the map and click **"Run Analysis"** to start the 5-stage ML pipeline. Wait a few seconds for the dashboard to refresh.
- *Optional (Live Tracking):* Use an **ngrok** tunnel mapped to port 8000 and pair it with the **OwnTracks** mobile app pointing via HTTP payload.
- *Optional (Chatbot):* Assign your `GEMINI_API_KEY` to the environment variables before starting the backend server to activate the AI natural language assistant.

## 📚 Detailed Documentation
Please refer to the comprehensive [PROJECT_DOCUMENTATION.md](./PROJECT_DOCUMENTATION.md) for a deep dive into:
- System logic and threat injection scenarios.
- Flowcharts and component architectures.
- Mathematical breakdowns of specific algorithms (DBSCAN, Isolation Forest, H3, Ray Casting).
- Full API endpoints list and Database Schema mappings.
- Complete File Structure.
- Teacher Questions & Answers for Viva prep.
