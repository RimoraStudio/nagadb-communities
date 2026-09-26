<p align="center">
  <img src="https://raw.githubusercontent.com/RimoraStudio/nagadb-communities/main/docs/logo.png" alt="NagaDB" width="120" />
</p>

<h1 align="center">NagaDB</h1>

<p align="center">
  A multi-tenant control plane for your databases. Self-hosted community edition<br/>
  distributed as a single Docker image — source available under BSL to commercial users.
</p>

<p align="center">
  <a href="https://github.com/RimoraStudio/nagadb-communities/releases"><img src="https://img.shields.io/github/v/release/RimoraStudio/nagadb-communities" /></a>
  <img src="https://img.shields.io/badge/engines-PostgreSQL%20%C2%B7%20MySQL%20%C2%B7%20MariaDB-336791" />
  <img src="https://img.shields.io/badge/docker-ghcr.io-blue" />
</p>

---

## Quickstart

```bash
curl -O https://raw.githubusercontent.com/RimoraStudio/nagadb-communities/main/docker-compose.yml
NAGADB_SECRET_KEY=$(openssl rand -hex 32) docker compose up -d
```

Open `http://localhost:4100` — sign up, and the first registered user becomes
the platform admin (`/admin`).

Or run directly:

```bash
docker run -d --name nagadb \
  -p 4100:4100 \
  -e NAGADB_SECRET_KEY="$(openssl rand -hex 32)" \
  -e NAGADB_EDITION=community \
  -v nagadb-data:/data \
  ghcr.io/rimorastudio/nagadb:latest
```

## What you get

- Register and operate PostgreSQL, MySQL, and MariaDB servers
- One-click databases, physical branching, per-table grants, managed DB users
- SQL workbench (tabs, autocomplete, EXPLAIN plans, saved queries, CSV/JSON export)
- Table browser + designer, objects browser (views/functions/triggers)
- Imports (`pg_dump`/`mysqldump` pipelines, CSV/JSON uploads), on-demand + scheduled backups
- SSH host provisioning — point it at a VM, get a managed Postgres
- Multi-org RBAC, scoped API keys, audit log, notifications
- Platform admin console (`/admin`) — users, orgs, billing ledger, maintenance mode
- Optional self-serve billing via Bakong KHQR checkout

## Configuration

All configuration is via environment variables — see `.env.example` for the full
list. Essentials: `NAGADB_SECRET_KEY` (required), `NAGADB_EDITION=community`,
optional `BAKONG_*` for KHQR checkout and `BACKUP_OFFLOAD_CMD` for offsite backups.

## Support & license

- Issues and feature requests: use GitHub Issues on this repo.
- Security reports: see `SECURITY.md`.
- The image is free for self-hosted/internal use. Source access and hosted-SaaS
  rights are available under a commercial license — see `LICENSE`.
