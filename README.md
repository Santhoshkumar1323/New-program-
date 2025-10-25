# mgnrega-dashboard-tamilnadu

This is the starter MVP for **Our Voice — Our Rights**: an MGNREGA District Dashboard (Tamil Nadu v0).
It includes a Dockerized frontend (React), backend (Node/Express), a Postgres schema, a Redis cache, and an ETL stub to fetch the data.gov.in MGNREGA API.

## Quick start (local)

1. Build and start services:
```bash
docker compose up --build -d
```

2. Import DB schema (after DB container is healthy):
```bash
container_id=$(docker ps -q -f "ancestor=postgres:15")
docker cp infra/schema.sql $container_id:/schema.sql
docker exec -it $container_id psql -U postgres -d mgnrega -f /schema.sql
```

3. Visit:
- Frontend: http://localhost
- Backend API: http://localhost:4000/api/districts

## Notes
- Replace `API_BASE` in `backend/src/etl/fetch_mgnrega.js` with the actual data.gov.in MGNREGA endpoint and map fields accordingly.
- For production: secure DB credentials, use SSL, configure Cloudflare or CDN, add monitoring and backups.

## Loom script
A short script for your 2-minute walkthrough is included in `LOOM_SCRIPT.txt`.
