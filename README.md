<div align="center">

# 🤖 AI Autonomous GPU Factory

**An AI-Powered Autonomous GPU Cluster Management System**

*Optimizing GPU Placement, Inference Routing, Distributed Training, Thermal Management & Power Consumption using Google Gemini AI.*

[![Status](https://img.shields.io/badge/status-active-success)](#)
[![Python](https://img.shields.io/badge/Python-3.10+-blue)](#)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green)](#)
[![React](https://img.shields.io/badge/React-18+-cyan)](#)
[![License](https://img.shields.io/badge/license-MIT-purple)](#)
[![Gemini](https://img.shields.io/badge/AI-Google%20Gemini-orange)](#)

[Features](#-features) • [Architecture](#-architecture) • [Tech Stack](#-tech-stack) • [Setup](#-quick-start) • [API Docs](#-api-endpoints) • [Screenshots](#-screenshots)

</div>

---

## 📖 Table of Contents

1. [Overview](#-overview)
2. [Key Features](#-features)
3. [System Architecture](#-architecture)
4. [Tech Stack](#-tech-stack)
5. [Project Structure](#-project-structure)
6. [Prerequisites](#-prerequisites)
7. [Quick Start](#-quick-start)
8. [Environment Variables](#-environment-variables)
9. [Database Schema](#-database-schema)
10. [API Endpoints](#-api-endpoints)
11. [AI Integration (Gemini)](#-ai-integration-gemini)
12. [Simulation Engine](#-simulation-engine)
13. [Frontend Guide](#-frontend-guide)
14. [Backend Guide](#-backend-guide)
15. [How It Works (Step-by-Step)](#-how-it-works-step-by-step)
16. [Testing](#-testing)
17. [Deployment](#-deployment)
18. [Troubleshooting](#-troubleshooting)
19. [Roadmap](#-roadmap)
20. [Learning Outcomes](#-learning-outcomes)
21. [Contributing](#-contributing)
22. [License](#-license)
23. [Acknowledgements](#-acknowledgements)

---

## 🌟 Overview

**AI Autonomous GPU Factory** is a full-stack practice project designed to simulate, manage, and optimize a virtual GPU cluster consisting of hundreds or thousands of GPUs.

In real-world data centers (like those operated by AWS, Google Cloud, or Microsoft Azure), managing thousands of GPUs is a massive operational challenge. You need to decide:
- **Which GPU** should run a specific workload?
- **How to route** inference requests to minimize latency?
- **How to schedule** distributed training across multiple GPUs?
- **How to prevent** overheating (thermal management)?
- **How to reduce** power consumption while maximizing throughput?

This project tackles all these challenges using a **multi-factor optimization algorithm** combined with **Google Gemini AI** for explainable decision-making.

Since the project is designed to run on **CPU-only laptops** (no expensive GPUs required), a **Virtual Cluster Simulation Engine** generates realistic GPU telemetry — temperatures, power draws, utilization, and health metrics — in real-time.

> **⚠️ Disclaimer:** This is a **practice/learning project**. It is **not** intended for production deployment. The simulation engine mimics real GPU behavior but is not connected to actual hardware.

---

## ✨ Features

### 🎯 1. Autonomous GPU Placement Optimization
The placement optimizer decides which GPU should host a new workload based on multiple factors:
- **Available Memory:** Does the GPU have enough VRAM for the model?
- **Thermal Headroom:** Is the GPU running cool enough?
- **Power Headroom:** Is the PSU capacity sufficient?
- **Current Load:** How busy is the GPU right now?
- **Network Topology:** How close is the GPU to data sources?

Each GPU is assigned a **weighted score**, and the top candidates are sent to **Gemini AI**, which provides a natural-language explanation of the decision.

### 🔀 2. Intelligent Inference Routing
When an inference request arrives, the router:
1. Filters out offline or overheated GPUs
2. Scores remaining GPUs based on:
   - Current queue depth
   - Average latency (last 60s)
   - Temperature
   - Power efficiency
3. Routes the request to the top-scored GPU
4. Logs the routing decision + AI explanation

### 🏋️ 3. Distributed Training Scheduler
For large-scale training jobs:
- Supports **2/4/8/16 GPU** configurations
- Automatically selects GPUs within the **same node** (for NVLink efficiency)
- Balances workloads to prevent resource starvation
- Tracks live training progress
- Handles mid-training failures (auto-restart on different GPUs)

### 🌡️ 4. Thermal Management
- Real-time temperature monitoring per GPU
- Configurable thermal thresholds (warning at 75°C, critical at 85°C)
- Automatic cooling simulation (fan speed, liquid cooling)
- Thermal alerts pushed to the frontend
- AI-powered thermal advisories

### ⚡ 5. Power Consumption Management
- Per-GPU and cluster-wide power tracking
- Efficiency score (performance-per-watt)
- Power anomaly detection
- AI recommendations for reducing power draw
- Historical power trends

### 🤖 6. AI Layer (Google Gemini)
The AI layer is the "brain" of the system. It provides:
- **AI Advisor:** Cluster health recommendations
- **Anomaly Detector:** Detects abnormal thermal/power patterns
- **Decision Engine:** Explains placement decisions in natural language
- **AI Chat Panel:** Ask natural language questions about the cluster

### 📊 7. Real-Time Dashboard
- Live stats grid (total GPUs, active jobs, cluster temp, power usage)
- GPU heatmap visualization
- Thermal & power charts (Recharts)
- Active jobs panel
- Alerts panel
- AI insights panel

### 🧪 8. Simulation Engine
Because the project runs on CPU-only machines:
- Simulates **16–32 virtual GPUs**
- Background scheduler updates telemetry every 2–5 seconds
- Realistic temperature curves (idle ~35°C, load ~75–85°C)
- Power draw scaling with utilization
- Randomized workload injection
- Failures and recoveries

---

## 🏗 Architecture

### High-Level Architecture Diagram

```text
┌─────────────────────────────────────────────────────────────┐
│                      REACT FRONTEND                         │
│  (Vite + TailwindCSS + Recharts + Framer Motion)            │
│                                                             │
│  ┌────────────┐  ┌────────────┐  ┌────────────────────┐     │
│  │ Dashboard  │  │  Placement │  │  AI Advisor Panel  │     │
│  └────────────┘  └────────────┘  └────────────────────┘     │
│  ┌────────────┐  ┌────────────┐  ┌────────────────────┐     │
│  │ GPU List   │  │ Thermal    │  │  Training Queue    │     │
│  └────────────┘  └────────────┘  └────────────────────┘     │
└──────────────────────────┬──────────────────────────────────┘
                           │ Axios / REST
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                     FASTAPI BACKEND                         │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  API Layer (v1 routers)                              │   │
│  │  Auth │ GPUs │ Nodes │ Placement │ Inference │ ...   │   │
│  └──────────────────────────────────────────────────────┘   │
│                           │                                 │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Service Layer                                       │   │
│  │  Business Logic, Validation, Orchestration           │   │
│  └──────────────────────────────────────────────────────┘   │
│                           │                                 │
│  ┌──────────────────┐  ┌────────────────────┐               │
│  │  Algorithms      │  │  AI Layer          │               │
│  │  - Placement     │  │  - Gemini Client   │               │
│  │  - Router        │  │  - Prompts         │               │
│  │  - Scheduler     │  │  - Advisor         │               │
│  │  - Thermal       │  │  - Anomaly Detect. │               │
│  │  - Power         │  │  - Decision Engine │               │
│  └──────────────────┘  └────────────────────┘               │
│                           │                                 │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Simulation Engine                                   │   │
│  │  - GPU Simulator │ Thermal │ Power │ Workloads       │   │
│  └──────────────────────────────────────────────────────┘   │
│                           │                                 │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Background Scheduler (APScheduler)                  │   │
│  │  - Telemetry updates │ Alert generation              │   │
│  └──────────────────────────────────────────────────────┘   │
└──────────────────────────┬──────────────────────────────────┘
                           │ SQLAlchemy ORM
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                      SQLITE DATABASE                        │
│  Tables: users, gpus, nodes, jobs, training_jobs,          │
│          inference_requests, thermal_readings,             │
│          power_readings, alerts                            │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                    EXTERNAL SERVICES                        │
│  - Google Gemini API (gemini-pro)                           │
└─────────────────────────────────────────────────────────────┘


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