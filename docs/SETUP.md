# Local setup

## Prerequisites
- Python version supported by the chosen FastAPI/Pydantic dependencies.
- Node.js LTS and npm.
- PostgreSQL.
- Git.

## Initial setup sequence
1. Create backend virtual environment and install `backend/requirements.txt`.
2. Copy `backend/.env.example` to `backend/.env`; fill local database credentials and any provider key locally.
3. Create the PostgreSQL database and run Alembic migrations.
4. Seed safe demo data using `backend/scripts/seed_demo_data.py`.
5. Install frontend dependencies in `frontend/`.
6. Copy `frontend/.env.example` to `frontend/.env` and set only the public backend base URL.
7. Start FastAPI and Vite using the commands documented in the root README.
8. Run backend and frontend tests, then follow `docs/DEMO_GUIDE.md`.

Never commit `.env`, credentials, uploaded private files, or real confidential brand material. Do not add a dependency or service without documenting why it is needed.
