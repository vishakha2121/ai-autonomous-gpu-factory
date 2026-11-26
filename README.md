# 🤖 AI Autonomous GPU Factory

> An AI-powered autonomous GPU cluster management system that optimizes GPU placement, inference routing, distributed training, thermal management, and power consumption — all powered by Google Gemini AI.

![Status](https://img.shields.io/badge/status-active-success)
![Python](https://img.shields.io/badge/Python-3.10+-blue)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green)
![React](https://img.shields.io/badge/React-18+-cyan)
![License](https://img.shields.io/badge/license-MIT-purple)
![Gemini](https://img.shields.io/badge/AI-Google%20Gemini-orange)

---

## 📖 Overview

**AI Autonomous GPU Factory** is a full-stack practice project that simulates and manages a virtual GPU cluster of thousands of GPUs. It uses **AI-driven decision making** (Google Gemini) to autonomously:

- 🎯 **Optimize GPU placement** for incoming workloads
- 🔀 **Route inference requests** to the best available GPU
- 🏋️ **Schedule distributed training** across multiple GPUs
- 🌡️ **Manage thermal** conditions and prevent overheating
- ⚡ **Optimize power consumption** and improve efficiency

Since this is a **practice project** designed to run on **CPU-only laptops**, a **virtual cluster simulation engine** generates realistic GPU telemetry (temperature, power, utilization) in real-time.

---

## ✨ Features

### 🎯 1. GPU Placement Optimization
- Multi-factor scoring algorithm (memory, thermal headroom, power headroom, current load)
- AI-generated explanation for *why* a particular GPU was chosen
- Visual placement board with drag-and-drop simulation

### 🔀 2. Inference Routing
- Smart routing to least-loaded, coolest, and lowest-latency GPU
- Real-time inference queue with route visualization
- Per-request latency tracking

### 🏋️ 3. Distributed Training
- Multi-GPU job scheduling (2 / 4 / 8 GPU configs)
- Live training progress tracking
- Automatic job rebalancing

### 🌡️ 4. Thermal Management
- Real-time temperature monitoring per GPU
- Threshold-based thermal alerts
- Cooling control simulation

### ⚡ 5. Power Consumption
- Per-GPU and cluster-wide power tracking
- Efficiency scoring
- Power anomaly detection

### 🤖 6. AI Layer (Gemini)
- **AI Advisor** — cluster health recommendations
- **Anomaly Detector** — detects abnormal thermal/power patterns
- **Decision Engine** — explains placement decisions in natural language
- **AI Chat Panel** — ask natural language questions about the cluster

### 📊 7. Real-Time Dashboard
- Live stats grid, GPU heatmap, thermal/power charts
- Active jobs panel, alerts panel, AI insights panel
- Beautiful dark futuristic UI with glassmorphism

### 🧪 8. Simulation Engine
- Virtual cluster of 16–32 simulated GPUs
- Background scheduler updating telemetry every 2–5 seconds
- Workload generator for realistic testing

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Python 3.10+, FastAPI, SQLAlchemy, Pydantic |
| **Database** | SQLite (practice-friendly, zero setup) |
| **AI** | Google Gemini API (`gemini-pro`) |
| **Frontend** | React 18, Vite, TailwindCSS |
| **Charts** | Recharts |
| **Animation** | Framer Motion |
| **Icons** | Lucide React |
| **Auth** | JWT (python-jose + passlib) |
| **HTTP Client** | Axios |
| **Routing** | React Router DOM v6 |

---

## 📁 Project Structure

```text
ai-autonomous-gpu-factory/
├── backend/          # FastAPI server + algorithms + AI layer
├── frontend/         # React + Vite + Tailwind UI
├── database/         # SQL schema + seed data
├── docs/             # API docs, architecture, setup guide
└── scripts/          # Setup & automation scripts


git clone https://github.com/vishakha2121/ai-autonomous-gpu-factory.git
cd ai-autonomous-gpu-factory


cd backend
python -m venv venv
source venv/bin/activate       # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env
# Add your GEMINI_API_KEY to .env
python run.py



cd frontend
npm install
cp .env.example .env
npm run dev