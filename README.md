# 🤖 InsureBot - Next-Gen AI Insurance Platform

[![FastAPI](https://img.shields.io/badge/Backend-FastAPI-009688.svg?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Next.js](https://img.shields.io/badge/Frontend-Next.js%2014-000000.svg?style=for-the-badge&logo=nextdotjs&logoColor=white)](https://nextjs.org)
[![Gemini](https://img.shields.io/badge/AI-Gemini%20Flash-4A90E2.svg?style=for-the-badge&logo=google&logoColor=white)](https://deepmind.google/technologies/gemini)
[![Supabase](https://img.shields.io/badge/Database-Supabase-3ECF8E.svg?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com)

**InsureBot** is a premium, AI-driven conversational insurance advisor designed to replace traditional complex Sales systems. By combining a **multimodal Gemini-powered AI Engine**, a **real-time streaming avatar interface**, and a **custom RAG (Retrieval-Augmented Generation)** knowledge system, InsureBot guides users through term insurance discovery, checks eligibility dynamically, and generates tailored PDF reports.

---

## ✨ Key Features

*   **🗣️ Interactive Streaming Avatar:** Immersive, low-latency conversational interface powered by **HeyGen Streaming Avatar** & **Simli SDK**.
*   **🧠 Intelligent AI Advisor:** Warm, emoji-rich, and contextual sales agent backed by **Gemini v2.0/v2.5 Flash** with custom system instructions.
*   **📊 Deterministic Needs Calculator:** Dynamic HLV (Human Life Value) calculation engine that checks liabilities and assets to recommend precise sum-assured limits.
*   **🔍 Local RAG Integration:** Searches claims metrics, synonym mappings, and term insurance eligibility rules from CSV and JSON databases.
*   **📄 PDF Report Generator:** Instantly builds and serves personalized PDF summaries featuring claims settlement ratios (CSR), solvency statistics, and tailored suitability notes.
*   **⚡ Modern Architecture:** Next.js 14 frontend styled with Tailwind CSS & Shadcn UI, paired with a high-performance FastAPI Python backend.

---

## 🛠️ Tech Stack

### Frontend
- **Framework:** Next.js 14 (TypeScript, App Router)
- **Styling:** Tailwind CSS, Framer Motion (micro-animations), Shadcn UI, Lucide Icons
- **Integrations:** `@heygen/streaming-avatar`, `simli-client`, `@supabase/supabase-js`

### Backend
- **Framework:** FastAPI, Uvicorn
- **AI/LLM:** Google Generative AI (`google-generativeai`)
- **Data Engineering:** Pandas, CSV, JSON
- **Report Engine:** FPDF (Custom PDF Layouts)
- **Database:** Supabase Client & Local SQLite

---

## 📁 Repository Structure

```tree
InsureBot/
├── frontend/                # Next.js Application
│   ├── app/                 # Next.js Pages & Routes
│   ├── components/          # Reusable UI Elements (Shadcn UI)
│   ├── public/              # Static Assets & Icons
│   └── package.json         # Frontend Dependency Configuration
│
└── backend/                 # FastAPI Application
    ├── main.py              # Main Application Server & API Routes
    ├── logic.py             # Insurance Engine & Needs Calculator
    ├── report_generator.py  # Custom PDF Report Layout Engine
    ├── pdf_logger.py        # Chat History to PDF Logger
    ├── supabase_client.py   # Admin Auth & Database Actions
    ├── requirements.txt     # Python Dependencies
    └── data/                # Local Knowledge & Database CSVs
        ├── brochures/       # Official Plan PDF Leaflets
        ├── policy_documents/# Detailed Policy Rules (PDF)
        └── Riders.csv       # Rider & Add-on Details Database
```

---

## 🚀 Getting Started

### 1. Backend Setup (FastAPI)

> [!IMPORTANT]
> Make sure you have **Python 3.10+** installed on your system.

Navigate to the `backend` folder:
```bash
cd backend
```

Create a `.env` file in the `backend` directory:
```env
GOOGLE_API_KEY=your_gemini_api_key_here
BASE_URL=http://127.0.0.1:8000
SUPABASE_URL=your_supabase_project_url
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key
```

Install dependencies and start the server:
```bash
# Install required libraries
pip install -r requirements.txt

# Run the FastAPI dev server
python main.py
```
*The API server will run at `http://127.0.0.1:8000`.*

---

### 2. Frontend Setup (Next.js)

Navigate to the `frontend` folder:
```bash
cd frontend
```

Install packages:
```bash
npm install
```

Start the Next.js development server:
```bash
npm run dev
```
*The client-side app will run at `http://localhost:3000` (or `http://localhost:5173` if configured as a SPA).*

---

## 🔒 Security & Underwriting Compliance
- **Anti-Hallucination Guardrails:** The AI is strictly barred from recommending policies outside the returned database matches, preventing ungrounded underwriting estimates.
- **Maximum Sum Assured Enforcer:** Limits calculations to a maximum of 15x–20x of the applicant's verified annual income, adhering to standard financial underwriting policies.
- **Client-Side Auth:** Bypasses server-side bottlenecks by writing chat and session state directly using the Supabase client-side JS library.
