# SalesGenie AI — Lead Management and Outreach Automation System

[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/)
[![Frontend](https://img.shields.io/badge/Frontend-Streamlit%201.32+-red.svg)](https://streamlit.io/)
[![Backend](https://img.shields.io/badge/Backend-FastAPI-green.svg)](https://fastapi.tiangolo.com/)
[![Database](https://img.shields.io/badge/Database-SQLite%20%7C%20SQLAlchemy-lightgrey.svg)](https://www.sqlite.org/)
[![Tests](https://img.shields.io/badge/Tests-12%2F12%20Passing-brightgreen.svg)]()
[![Internship](https://img.shields.io/badge/Infosys%20Springboard-Team%20C-orange.svg)]()

> **Infosys Springboard Technical Internship Program 2026**  
> **Project:** Lead Management and Outreach Automation System (SalesGenie AI)  
> **Squad:** Team C  
> **Role:** Frontend Developer  
> **Contributor:** Mahek Saba Shaikh  

---

## 📌 Executive Summary

**SalesGenie AI** is an intelligent, autonomous B2B lead management and outreach automation platform engineered to streamline the full sales pipeline lifecycle — from raw lead ingestion and AI-driven qualification scoring to hyper-personalized email outreach generation, conversation summarization, and CRM synchronization monitoring.

This repository hosts the **Frontend Application** along with the integrated backend API client, automated test suites, and project documentation for **Milestone 1, Milestone 2, and Milestone 3**.

---

## 🚀 Key Functional Modules & Features

### 1. 📊 Executive Analytics Dashboard
* **Real-time KPI Tiles:** Immediate visibility into Total Ingested Prospects, Hot Leads, Warm Leads, Cold Leads, and Pipeline Conversion Rate.
* **Secondary Velocity Metrics:** Tracks outreach campaigns drafted, call interaction logs, and pipeline velocity.
* **Interactive Visualizations:** Priority breakdown charts, industry vertical distributions, and the **Top Ranked Prospects Leaderboard** dynamically sorted by AI qualification score.
* **Executive Summary Widgets:** Integrated CRM synchronization telemetry and live activity feed digest for quick status assessment.

### 2. 👥 Leads Management Dashboard (Milestone 1)
* **Lead Directory & Tabular View:** Comprehensive overview of all stored prospects with company name, contact person, email, industry, company size, and status.
* **Smart Search & Filters:** Instant filtering by lead status (`New`, `Contacted`, `Qualified`, `Closed`), industry verticals, and search queries.
* **Manual Lead Ingestion:** Form-based lead creation with field validation and immediate backend persistence.
* **Bulk CSV Import:** High-throughput batch ingestion supporting CSV schemas with automated format validation and preview before ingest.

### 3. 🧠 Lead Intelligence & Scoring (Milestone 2)
* **Company Profile Deep-Dive:** Automated analysis of business needs, potential pain points, key opportunities, and industry market positioning.
* **Algorithmic Lead Qualification Scoring:** Computes objective qualification scores (0–100) based on company size, industry alignment, and buying intent.
* **Four-Tier Classification:** Categorizes prospects into distinct priority tiers:
  * 🔥 **Very Hot (80–100):** Immediate high-priority engagement.
  * ⚡ **Hot (65–79):** High-potential prospect.
  * 🌤️ **Warm (50–64):** Standard follow-up nurture track.
  * ❄️ **Cold (< 50):** Long-term awareness campaign.

### 4. ✉️ AI-Powered Outreach Generator (Milestone 2)
* **Context-Aware Email Drafting:** Generates hyper-personalized cold outreach emails tailored to the specific lead's industry, company size, and business needs.
* **Strategic Copywriting Elements:** Dynamically drafts high-converting Subject Lines, Body Copy, Value Propositions, and clear Calls-to-Action (CTA).
* **Tone & Persona Customization:** Configurable messaging angles (Value-Focused, Consultative, Direct).
* **Truthful Delivery Architecture:** Verifies SMTP credentials before sending; guarantees no false-positive "Email Sent" confirmations when SMTP servers are unconfigured.

### 5. 💬 Conversation Intelligence & Meeting Summary (Milestone 3)
* **Call Transcript Processing:** Ingests raw call notes and audio meeting transcripts to extract high-value conversation insights.
* **NLP Summarization via `POST /intelligence/conversation`:**
  * **Executive Call Summary Card:** Highlights company context, discussed pain points, and evaluation timelines.
  * **Action Items Checklist:** Interactive checkable UI with owners and due dates.
  * **Key Takeaways & Decisions:** Bulleted breakdown of discussed features and requirements.
  * **Recommended Next Steps:** Prescriptive follow-up directives.
* **Sample Transcript Auto-Loader:** One-click sample enterprise discovery call ("Sarah Johnson - TechCorp Solutions") for quick demonstration.
* **Export Utility:** One-click copy-to-clipboard code block formatted for instant sharing to Slack, Notion, or email.

### 6. 🔄 CRM Synchronization Status Monitor (Milestone 3)
* **Live System Telemetry:** Live probes to backend `/health` and CRM synchronization services.
* **Telemetry Metrics:** Displays real-time metrics for *Queued Prospects*, *Successfully Synced Records*, *Failed / Stalled Sync Events*, and *Target CRM Engine*.
* **Field Mapping Schema Table:** Transparent bidirectional dictionary mapping local fields (`Lead ID`, `Company Name`, `Contact Email`, `Lead Score`, `Qualified Tier`, `Outreach Stage`) to standard CRM Contact and Deal properties (HubSpot / Salesforce).
* **Truthful Manual Sync Trigger:** An interactive sync trigger button that reports actual backend status truthfully without falsifying success.

### 7. ⚡ Real-Time Activity Feed (Milestone 3)
* **Chronological Audit Trail:** Dynamically synthesized activity stream aggregating genuine backend records (`leads_cache` timestamps, scoring events, and conversation sessions).
* **Category Filter Pills:** Instant filtering by *All Activities*, *Leads Ingested*, *Intelligence & Scoring*, *Outreach Generated*, or *Conversations*.
* **Glassmorphic Timeline UI:** Modern UI cards featuring color-coded dot badges, actor identifiers, relative timestamps, and expandable payload details.

---

## 🛠️ Architecture & Technology Stack

```
┌────────────────────────────────────────────────────────┐
│                   STREAMLIT FRONTEND                   │
│              (app.py - Glassmorphism UI)               │
└───────────────────────────┬────────────────────────────┘
                            │ HTTP Requests / JSON
┌───────────────────────────▼────────────────────────────┐
│                    FASTAPI BACKEND                     │
│                (main.py - REST Endpoints)              │
├───────────────────────────┬────────────────────────────┤
│   Company Intelligence    │   Lead Scoring Engine      │
│   Outreach Generator      │   Conversation Summarizer  │
└───────────────────────────┬────────────────────────────┘
                            │ SQLAlchemy ORM
┌───────────────────────────▼────────────────────────────┐
│                  SQLITE DATABASE ENGINE                │
│                     (salesgenie.db)                    │
└────────────────────────────────────────────────────────┘
```

| Layer | Technologies Used |
| :--- | :--- |
| **Frontend Client** | Streamlit 1.32+, Custom CSS Injection, Pandas, Requests |
| **Backend API** | FastAPI, Uvicorn (ASGI Server), Pydantic v2 |
| **Database & ORM** | SQLite 3, SQLAlchemy 2.0 |
| **NLP & AI Engine** | OpenAI API / Local Rule-Based NLP & Summarization Heuristics |
| **Testing & CI** | Python `unittest` framework |

---

## 🔗 Integrated Backend API Endpoints

| Endpoint | Method | Functional Module | Frontend Usage |
| :--- | :---: | :--- | :--- |
| `/leads/` | `GET` | Lead Management | Fetches prospect directory for tables, dropdowns, and metrics |
| `/leads/` | `POST` | Lead Ingestion | Submits single new lead form data |
| `/leads/bulk` | `POST` | Bulk Ingestion | Transmits parsed CSV rows for batch insertion |
| `/intelligence/analyze/{id}` | `POST` | Lead Intelligence | Generates company profile analysis and pain points |
| `/intelligence/score/{id}` | `POST` | Qualification Scoring | Calculates qualification score and tier |
| `/intelligence/outreach` | `POST` | Outreach Automation | Drafts hyper-personalized cold outreach emails |
| `/intelligence/conversation` | `POST` | Conversation Intelligence | Summarizes call transcripts into action items and key points |
| `/analytics/dashboard` | `GET` | Analytics Dashboard | Fetches aggregated KPIs, leaderboard, and charts |
| `/health` | `GET` | System Telemetry | Probes backend uptime and CRM service connectivity |

---

## 💻 Installation & Setup Guide

### 1. Prerequisites
* Python 3.10 or Python 3.11 installed
* Git installed

### 2. Clone the Repository
```bash
git clone https://github.com/Mahek-saba/frontend-infosys.git
cd frontend-infosys
git checkout feature/milestone-3-frontend
```

### 3. Create a Virtual Environment & Install Dependencies
```bash
python -m venv venv
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

pip install -r requirements.txt
```

### 4. Run Both Backend & Frontend Simultaneously
Use the all-in-one launcher script:
```bash
python run_all.py
```
Or start each service in separate terminals:
```bash
# Terminal 1: Backend API (FastAPI)
python -m uvicorn main:app --host 127.0.0.1 --port 8000 --reload

# Terminal 2: Frontend Dashboard (Streamlit)
python -m streamlit run app.py --server.port 8501
```

* **Frontend Dashboard:** [http://localhost:8501](http://localhost:8501)
* **Backend API Docs (Swagger UI):** [http://localhost:8000/docs](http://localhost:8000/docs)

---

## 🧪 Automated Testing & Validation

The test suite validates both API functionality and frontend data contracts:

```bash
python -m unittest tests/test_frontend_and_api.py -v
```

### Test Results Summary:
* ✅ `test_01_health_endpoint`: Backend uptime and service status validation.
* ✅ `test_02_lead_listing`: Lead retrieval and schema compliance.
* ✅ `test_03_lead_creation_and_validation`: Ingestion validation with required fields.
* ✅ `test_04_csv_bulk_import_validation`: Batch tabular ingestion handling.
* ✅ `test_05_company_analysis`: Business needs and opportunity extraction.
* ✅ `test_06_lead_scoring_and_thresholds`: Strict adherence to Very Hot / Hot / Warm / Cold scoring criteria.
* ✅ `test_07_outreach_email_generation`: Subject line, body copy, and value proposition verification.
* ✅ `test_08_send_email_truthfulness_check`: Verifies no false-positive email delivery without configured SMTP.
* ✅ `test_09_dashboard_analytics`: Dashboard KPI and leaderboard calculations.
* ✅ `test_10_sample_csv_validity`: Schema validation of `sample_leads.csv`.
* ✅ `test_11_conversation_intelligence_summarization`: Milestone 3 call transcript summarization & action-item generation.
* ✅ `test_12_crm_sync_endpoint_truthfulness`: Milestone 3 unconfigured CRM sync endpoint handling.

**12/12 Tests Passing (100% Success Rate in 0.25s).**

---

## 📂 Project Directory Structure

```
├── .streamlit/
│   └── config.toml           # Theme, color palettes, and server settings
├── database/
│   ├── __init__.py
│   └── models.py             # SQLAlchemy ORM models (Lead, Company, Conversation)
├── modules/
│   ├── module1_lead_capture.py
│   ├── module2_company_analysis.py
│   ├── module3_lead_scoring.py
│   ├── module4_outreach.py
│   └── module5_conversation.py # Call transcript summarization logic
├── tests/
│   └── test_frontend_and_api.py # Automated test suite (12 tests)
├── Internship_Report/        # Formal documentation and screenshots
│   ├── INTERNSHIP_TECHNICAL_REPORT.md
│   ├── Internship_Technical_Report_Mahek_Saba_Shaikh.docx
│   └── screenshots/          # High-resolution UI captures
├── app.py                    # Main Streamlit Frontend application
├── main.py                   # FastAPI backend server application
├── requirements.txt          # Python dependencies
├── run_all.py                # Dual service launcher script
├── salesgenie.db             # Local SQLite database
├── sample_leads.csv          # Sample lead ingestion dataset
└── README.md                 # Project documentation
```

---

## 👥 Contributor & Acknowledgement

* **Student Developer:** Mahek Saba Shaikh
* **Role:** Frontend Developer (Team C)
* **Internship Program:** Infosys Springboard Technical Internship 2026
* **Organization:** Infosys Springboard

Special thanks to the Infosys Springboard mentors and Team C peers for guidance and collaboration throughout this internship project.
