# GeM Saarthi

**SIH26100 — Evidence-first bid compliance for GeM procurement**

GeM Saarthi is a demo-ready, full-stack prototype that converts tender requirements into structured rules, links bidder evidence to those rules, detects contradictions, evaluates compliance deterministically, and keeps the final procurement decision with an authorised officer.

> **AI proposes. Evidence proves. Rules evaluate. Officers decide.**

This repository intentionally uses a deterministic demo processor so the core SIH workflow works without external AI/OCR credentials. AI/OCR integrations can be added behind service adapters later.

## Stack

- Frontend: React + Vite + TypeScript + Recharts + Lucide
- Backend: FastAPI + SQLAlchemy + JWT + bcrypt
- Local database: SQLite by default
- Team/server database: PostgreSQL via Docker Compose

## Run on Windows (fastest path)

### 1. Start backend

```powershell
cd gem-saarthi\backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python -m app.db.seed
uvicorn app.main:app --reload --port 8000
```

### 2. Start frontend (new PowerShell)

```powershell
cd gem-saarthi\frontend
npm install
npm run dev
```

Open **http://localhost:5173**.

Backend docs: **http://localhost:8000/docs**  
Health: **http://localhost:8000/api/health**

## Demo accounts

All seeded demo accounts use `Demo@12345`:

- officer@gemsaarthi.demo
- admin@gemsaarthi.demo
- operator@gemsaarthi.demo

Use the **Officer** account for the end-to-end SIH demonstration.

## The judge demo

1. Sign in as Procurement Officer.
2. Open the seeded bid from the Live case queue.
3. Review the proposed local-content requirement.
4. Approve the rule.
5. Run deterministic evaluation.
6. Show evidence: bidder declaration **55%** vs certificate **45%**.
7. Show the resulting **CONTRADICTION / Officer review** finding.
8. Record **Clarify** as the officer decision.
9. Use the dashboard/audit data as the traceability story.

## Repository layout

```text
gem-saarthi/
├── backend/
│   ├── app/
│   │   ├── api/
│   │   ├── core/
│   │   ├── db/
│   │   ├── models/
│   │   ├── schemas/
│   │   └── services/
│   └── tests/
├── frontend/
│   └── src/
├── docker-compose.yml
├── .env.example
├── SECURITY.md
└── README.md
```

## GitHub

```powershell
git init
git add .
git commit -m "Build GeM Saarthi SIH prototype"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/gem-saarthi.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your own GitHub account.

## Docker / PostgreSQL

The included Compose file provides PostgreSQL plus a containerized backend. The fastest student demo is the SQLite path above; use Compose for team/server development.

## Government-readiness note

The UI intentionally describes GeM Saarthi as a **proposed digital platform / SIH demo environment**. Do not represent it as an officially approved Government of India, NIC, MeitY, or GeM production system unless you obtain those approvals.
