# Hello World — React + FastAPI

Minimal test app. Frontend on **3083**, backend on **8083**.

## Backend (port 8083)

```bash
cd backend
python -m venv .venv
.venv/Scripts/python.exe -m pip install -r requirements.txt   # Windows
.venv/Scripts/python.exe -m uvicorn main:app --host 127.0.0.1 --port 8083 --reload
```

Endpoint: `GET http://127.0.0.1:8083/api/hello`

## Frontend (port 3083)

```bash
cd frontend
npm install
npm run dev
```

Open http://127.0.0.1:3083

`/api` is proxied to the backend by Vite, so the frontend uses a relative
`fetch('/api/hello')` and there is no cross-origin call in dev.

## Note on Windows

Vite is pinned to `host: '127.0.0.1'` in `vite.config.js`. Without it, Vite
binds IPv6-only (`[::1]`) on Windows while uvicorn binds IPv4, so
`http://127.0.0.1:3083` refuses connections.
