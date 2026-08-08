# GridLift AI

GridLift AI is a sensorless Dynamic Line Rating engine that uses weather data, SCADA-style current data, and physics-informed modeling to reveal hidden transmission capacity and unlock curtailed renewable energy.

## MVP Features

- Live weather ingestion from Open-Meteo
- Simplified IEEE 738-inspired thermal model
- Real-time conductor temperature estimation
- Static vs dynamic line rating comparison
- Dispatch advisory signal
- Curtailment savings tracker
- Demo gust trigger for reliable live demo

## Quickstart

### 1. Backend

```bash
cd backend
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --reload --port 8000

Backend endpoints:

http://localhost:8000/
http://localhost:8000/health
http://localhost:8000/state
http://localhost:8000/stream

###Trigger demo gust:

curl -X POST http://localhost:8000/demo/gust \
  -H "Content-Type: application/json" \
  -d '{"duration_s": 240, "target_wind_mps": 15}'

###Reset demo:
curl -X POST http://localhost:8000/demo/reset

### 2.Frontend
cd frontend
npm install
npm run dev

Open:
http://localhost:5173
