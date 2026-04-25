# Knowledge Compiler

A small product scaffold for turning raw text into canonical patterns, a knowledge graph, and a queryable backend + UI.

## Stack
- FastAPI
- Celery + Redis
- PostgreSQL
- Next.js + Tailwind

## Local run

### Backend
```bash
cd backend
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### Worker
```bash
cd backend
celery -A app.workers.celery_app.celery_app worker --loglevel=info
```

### Frontend
```bash
cd frontend
npm install
npm run dev
```

### Infra
```bash
docker compose up --build
```

## Environment
Copy the example env files and set:
- DATABASE_URL
- REDIS_URL
- NEXT_PUBLIC_API_BASE_URL

## What it does
1. Upload or paste text
2. Queue a compile job
3. Extract subject / relation / object patterns
4. Canonicalize and deduplicate
5. Store patterns and edges
6. Query the compiled knowledge
