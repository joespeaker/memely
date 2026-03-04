# Memely

API-first platform for searchable, shareable reaction and meme images.

## Repository layout

- `apps/api` - API contracts and backend implementation entrypoint
- `apps/web` - web client entrypoint
- `workers/processor` - async processing workers
- `infra` - deployment and infrastructure stubs
- `docs` - architecture, policy, and operations docs

## Quick start

1. Copy `.env.example` to `.env` and fill values.
2. Implement API server from `apps/api/openapi.yaml`.
3. Run migrations in `apps/api/migrations`.
