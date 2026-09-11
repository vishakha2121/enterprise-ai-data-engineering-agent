# 🤖 Enterprise AI Data Engineering Agent

> An intelligent, AI-powered Data Engineering Agent that automatically builds ETL pipelines, validates datasets, detects schema drift, creates transformations, and schedules workflows — all through natural language.

![Status](https://img.shields.io/badge/status-active-success)
![Python](https://img.shields.io/badge/python-3.10+-blue)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green)
![React](https://img.shields.io/badge/React-18-61DAFB)
![Gemini](https://img.shields.io/badge/Gemini-AI-orange)
![License](https://img.shields.io/badge/license-MIT-blue)

---

## 📖 Overview

**Enterprise AI Data Engineering Agent** is a practice/learning project that demonstrates how AI agents can be applied to real-world **Data Engineering** workflows. Instead of manually writing ETL scripts, users describe what they want in plain English, and the AI Agent automatically:

- 🏗️ **Generates ETL pipelines** (Extract → Transform → Load)
- ✅ **Validates datasets** (nulls, types, ranges, uniqueness)
- 🔍 **Detects schema drift** (compares current vs historical schema)
- 🔄 **Creates transformations** (clean, cast, aggregate, join)
- ⏰ **Schedules workflows** (cron-based automation)
- 💬 **Chats with you** like a senior data engineer

Built with a modern stack: **FastAPI** backend, **Google Gemini** AI brain, **PySpark** for processing, **SQL** for metadata, and a beautiful **React** dashboard.

---

## ✨ Features

### 🧠 AI Agent (Powered by Google Gemini)
- Natural language → ETL pipeline generation
- Function calling / tool use (creates real pipelines, not just text)
- Conversation memory (remembers context)
- Explains its reasoning step-by-step

### 🏗️ ETL Pipeline Builder
- Visual + AI-generated pipelines
- Support for CSV, JSON, Parquet
- Extract → Transform → Load stages
- Real-time execution logs (WebSocket)

### ✅ Dataset Validation
- Auto-detect data types
- Null / duplicate / range checks
- Custom rule engine
- Detailed validation reports

### 🔍 Schema Drift Detection
- Snapshot schemas over time
- Diff viewer (added/removed/changed columns)
- Alert on breaking changes

### 🔄 Transformations
- Filter, map, cast, aggregate, join
- Preview before applying
- Reusable transformation library

### ⏰ Workflow Scheduling
- Cron-based scheduling
- APScheduler-powered (lightweight)
- Run history + retry logic

### 📊 Beautiful Dashboard
- Real-time stats
- Pipeline health charts
- Recent activity feed
- Dark mode UI

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18, Vite, Tailwind CSS, shadcn/ui, Recharts, Zustand |
| **Backend** | Python 3.10+, FastAPI, SQLAlchemy, Pydantic |
| **AI** | Google Gemini API (`google-generativeai`) |
| **Data Processing** | PySpark (local mode) |
| **Database** | SQLite (dev) / PostgreSQL (optional) |
| **Scheduler** | APScheduler |
| **Streaming** | Kafka (optional) / In-memory queue |
| **Orchestration** | Airflow DAG templates (generated) |
| **Real-time** | WebSocket |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│                   React Dashboard                    │
│   Dashboard • Pipelines • Datasets • Agent Chat      │
└──────────────────────┬──────────────────────────────┘
                       │ REST + WebSocket
┌──────────────────────▼──────────────────────────────┐
│                  FastAPI Backend                     │
│  ┌──────────────────────────────────────────────┐   │
│  │           AI Agent (Gemini)                   │   │
│  │   Prompts • Tools • Memory • Reasoning        │   │
│  └──────────────────────────────────────────────┘   │
│  ┌───────────┐ ┌───────────┐ ┌─────────────────┐   │
│  │ Services  │ │  Engine   │ │   Scheduler     │   │
│  │ Layer     │ │ (Spark/   │ │ (APScheduler)   │   │
│  │           │ │  SQL/     │ │                 │   │
│  │           │ │  Kafka)   │ │                 │   │
│  └───────────┘ └───────────┘ └─────────────────┘   │
└──────────────────────┬──────────────────────────────┘
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
   ┌─────────┐   ┌─────────┐   ┌──────────┐
   │ SQLite  │   │  Files  │   │  Spark   │
   │  (Meta) │   │ (Data)  │   │ (Local)  │
   └─────────┘   └─────────┘   └──────────┘
```

---

## 🚀 Quick Start

### Prerequisites
- Python 3.10+
- Node.js 18+
- Google Gemini API Key ([Get free](https://aistudio.google.com/app/apikey))

### 1. Clone
```bash
git clone https://github.com/vishakha2121/enterprise-ai-data-engineering-agent.git
cd enterprise-ai-data-engineering-agent
```

### 2. Backend Setup
```bash
cd backend
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt

# Add your Gemini API key
cp .env.example .env
# Edit .env and add: GEMINI_API_KEY=your_key_here

# Initialize database
python scripts/setup_db.py

# Run backend
uvicorn app.main:app --reload --port 8000
```

### 3. Frontend Setup
```bash
cd frontend
npm install
cp .env.example .env
npm run dev
```

### 4. Open
- **Frontend:** http://localhost:5173
- **API Docs:** http://localhost:8000/docs

---

## 📸 Screenshots

> *(Add screenshots after building)*

| Dashboard | AI Agent Chat |
|-----------|---------------|
| ![Dashboard](docs/screenshots/dashboard.png) | ![Agent](docs/screenshots/agent_chat.png) |

| Pipelines | Schema Diff |
|-----------|-------------|
| ![Pipelines](docs/screenshots/pipelines.png) | ![Schema](docs/screenshots/schema_view.png) |

---

## 🎯 Use Cases

1. **"Create an ETL pipeline that reads sales.csv, removes nulls, and loads into Postgres"** → AI generates + runs it
2. **"Validate my customers dataset"** → Full quality report in seconds
3. **"My schema changed — what broke?"** → Drift report with breaking changes highlighted
4. **"Schedule this pipeline every day at 2 AM"** → Cron registered automatically

---

## 📁 Project Structure

```
enterprise-ai-data-engineering-agent/
├── backend/          # FastAPI + AI Agent + Engine
├── frontend/         # React + Tailwind UI
├── database/         # SQL migrations + seeds
├── docs/             # Architecture, API refs, screenshots
└── infrastructure/   # Docker, scripts
```

*(Full structure in `docs/ARCHITECTURE.md`)*

---

## 🧪 Testing

```bash
# Backend
cd backend
pytest

# Frontend
cd frontend
npm run test
```

---

## 🗺️ Roadmap

- [x] Core AI agent with Gemini
- [x] ETL pipeline generation
- [x] Dataset validation
- [x] Schema drift detection
- [x] Workflow scheduling
- [ ] Multi-user support + auth
- [ ] Real Kafka integration
- [ ] Airflow DAG deployment
- [ ] Cloud deployment (AWS/GCP)

---

## ⚠️ Disclaimer

This is a **practice/learning project** built to explore AI agents in Data Engineering. It uses **lightweight local setups** (PySpark local mode, SQLite, APScheduler) instead of full production clusters. Not intended for enterprise production use without hardening.

---

## 🙏 Acknowledgements

- [Google Gemini API](https://ai.google.dev/) for the AI brain
- [FastAPI](https://fastapi.tiangolo.com/) for the backend framework
- [shadcn/ui](https://ui.shadcn.com/) for beautiful components
- [Apache Spark](https://spark.apache.org/) for data processing

---

## 📜 License

MIT License — see [LICENSE](LICENSE) file.

---

## 👨‍💻 Author

**Vishakha**
- GitHub: [@vishakha2121](https://github.com/vishakha2121)

---

⭐ **If you found this project interesting, give it a star!**


