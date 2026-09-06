# GeM Saarthi Backend

FastAPI API for the GeM Saarthi SIH26100 prototype. Defaults to SQLite for a one-command local demo; set `DATABASE_URL` to PostgreSQL for a team/server environment.

## Run

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python -m app.db.seed
uvicorn app.main:app --reload --port 8000
```

Docs: http://localhost:8000/docs
