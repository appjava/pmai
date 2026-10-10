# 🌱 PMAI - Intelligent Agroecological Monitoring Platform

[![Status](https://img.shields.io/badge/Status-In%20Development-yellow)](https://pmai-saas.web.app)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Qwen AI Integration](https://img.shields.io/badge/AI-Qwen%20Powered-purple)](https://qwenlm.github.io/)

**PMAI** is an open-source SaaS solution designed to empower small-scale agroecological producers and agricultural SMEs in Latin America. It enables real-time monitoring of environmental variables (soil moisture, temperature, luminosity), early warning alerts, and sustainability reporting, even in rural areas with limited connectivity.

🔗 **Live Demo:** [https://pmai-saas.web.app](https://pmai-saas.web.app)


## 🚀 Key Features (MVP)
- ✅ **Mobile-First Interactive Dashboard:** Real-time visualization of sensor data.
- ✅ **Crop & Device Management:** Logical grouping of IoT nodes per cultivation zone.
- ✅ **Smart Alert Engine:** Email notifications based on customizable thresholds.
- ✅ **Offline-First Architecture:** Local data caching with background sync when connectivity is restored.
- ✅ **Sustainability Reports:** Exportable CSV/PDF reports for organic certification tracking.


## 🤖 Qwen AI Integration (Roadmap)
PMAI is actively evolving to integrate **Qwen's open-source LLM capabilities** to democratize precision agriculture:
1. **Predictive Crop Analysis:** Fine-tuning Qwen to analyze historical sensor patterns and predict irrigation needs or frost risks.
2. **NLP Agricultural Assistant:** A Spanish/English chatbot allowing farmers with low technical literacy to query data naturally (e.g., *"¿Cómo estuvo la humedad en el Vivero ayer?"*).
3. **Automated Executive Reports:** Generating plain-language sustainability summaries from raw JSON sensor data.
4. **Anomaly Detection:** Identifying early signs of pests or diseases by correlating temperature, humidity, and luminosity spikes.

*We plan to contribute our agricultural prompt engineering datasets and fine-tuning scripts back to the Qwen community.*


## 🛠️ Tech Stack
| Layer | Technology | Justification |
|-------|------------|---------------|
| **Frontend** | React.js, TypeScript, Vite, Tailwind CSS | Fast, modern, excellent mobile-first support. |
| **Backend** | Python, FastAPI | High-performance, asynchronous, ideal for IoT APIs. |
| **Database** | SQLite (Dev) / PostgreSQL + Supabase (Prod) | Robust, open-source, excellent time-series support. |
| **Infrastructure** | Cloudflare Pages, GitHub Actions | Zero-cost, global CDN, automated CI/CD. |
| **Hardware** | ESP32, DHT11, Soil Moisture Sensors | Low-cost, solar-compatible, Wi-Fi/Bluetooth enabled. |


## 🏗️ Architecture

```text
┌─────────────────────────────────────────────────────────┐
│  DEVELOPMENT (Local)                                    │
│  Frontend: React (localhost:3000)                       │
│  Backend:  FastAPI (localhost:8000)                     │
│  Database: SQLite (Lightweight, zero RAM impact)        │
└─────────────────────────────────────────────────────────┘
                          │ Git Push / CI/CD
                          ▼
┌─────────────────────────────────────────────────────────┐
│  PRODUCTION (Cloud)                                     │
│  Frontend: Cloudflare Pages → pmai-saas.dev             │
│  Backend:  Railway/Render → api.pmai-saas.dev           │
│  Database: Supabase (PostgreSQL 500MB Free Tier)        │
│  AI Layer: Qwen API (Future Phase)                      │
└─────────────────────────────────────────────────────────┘

```

## 💻 Featured Code: Smart Alert Engine
Here is a snippet of the backend logic that evaluates incoming sensor readings against user-defined thresholds to trigger alerts:

```python
# app/services/alert_engine.py
from app.models.database import Alerta, Umbral, LecturaSensor
from app.core.config import settings

async def evaluate_alerts(lectura: LecturaSensor, umbrales: list[Umbral]) -> list[Alerta]:
    """Evaluates sensor readings against configured thresholds and generates alerts."""
    alertas = []
    
    for umbral in umbrales:
        # Dynamically get the sensor value based on the threshold variable
        valor = getattr(lectura, umbral.variable.lower(), None)
        
        if valor is not None:
            if valor < umbral.valor_minimo or valor > umbral.valor_maximo:
                severity = "Crítica" if valor < (umbral.valor_minimo * 0.8) else "Advertencia"
                
                nueva_alerta = Alerta(
                    tipo_alerta=severity,
                    mensaje=f"{umbral.variable} fuera de rango: {valor}",
                    variable_violada=umbral.variable,
                    valor_detectado=valor,
                    id_umbral=umbral.id_umbral,
                    id_lectura=lectura.id_lectura
                )
                alertas.append(nueva_alerta)
                
    return alertas

```
## 🚀 Getting Started (Local Development)

1. Clone the repository:
```bash
git clone https://github.com/appjava/pmai-mvp.git
cd pmai-mvp
```
2. Backend Setup:
```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```
3. Frontend Setup:
```bash
cd ../frontend
npm install
npm run dev
```

## 👨‍💻 Author & Community
**Jaime Alberto Valencia Abadía**
Mechanical Engineer (10+ years) & Software Development Technologist (SENA).
Building sustainable tech solutions, one sensor, script, and circuit at a time.

🌐 Portfolio: [appjava.pages.dev](https://appjava.pages.dev)

📧 Contact: java8934692@soy.sena.edu.co

## 🤝 Contributing
We welcome contributions from the open-source community! Whether you want to fix a bug, improve the UI, or help integrate Qwen AI, please read our Contributing Guidelines before submitting a Pull Request.
