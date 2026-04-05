---
name: project-context
description: Provides shared project context for all FastAPI agents — environment, database settings, and service URLs.
---

# Skill: Project Context

Shared project context for all agents working on the Ram Rajya Society System backend (FastAPI).

## Environment

- **API Base URL**: {{API_BASE_URL}}
- **Environment**: development | staging | production
- **CORS Allowed Origins**: {{CORS_ORIGINS}}

## Database Settings (PostgreSQL/MySQL)

- **DB Host**: {{DB_HOST}}
- **DB Name**: {{DB_NAME}}
- **DB User**: {{DB_USER}}
- **Schema Reference**: `app/models/`

## Authentication

- **Algorithm**: HS256
- **Access Token Expire Minutes**: 30
- **OAuth2 Scopes**: admin, user, read-only

## Project Architecture

```text
app/
├── main.py              <- Entry point (FastAPI instance)
├── api/
│   └── v1/             <- Versioned routes
├── core/               <- Security, Config, Logging
├── models/             <- ORM models (SQLAlchemy)
├── schemas/            <- Pydantic models (Input/Output)
├── crud/               <- Database operations
└── tests/              <- Pytest suite
```

## Key API Endpoints

| Resource | Base Path | Description |
|----------|-----------|-------------|
| Auth | `/auth` | Login, Logout, Token Refresh |
| Users | `/users` | User management |
| Societies | `/societies` | RAM Rajya Society entities |
| ... | ... | ... |
