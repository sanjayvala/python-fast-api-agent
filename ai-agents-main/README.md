# Claude Code FastAPI Agents & Skills

A reusable collection of Claude Code agents and skills for Python FastAPI backend development.

## Setup Instructions

### 1. Copy to Your Project

Copy the `agents/` and `skills/` folders into your project's `.claude/` directory:

```bash
cp -r agents/ /path/to/your-project/.claude/agents/
cp -r skills/ /path/to/your-project/.claude/skills/
```

### 2. Configure Your Environment

Replace the placeholder values in `skills/project-context/SKILL.md` with your actual project details.

| Placeholder | Description | Example |
|---|---|---|
| `{{API_BASE_URL}}` | Your local API base URL | `http://localhost:8000` |
| `{{DB_HOST}}` | Database host | `localhost` |
| `{{DB_NAME}}` | Database name | `ram_rajya_db` |
| `{{DB_USER}}` | Database user | `postgres` |

## Included Agents

| Agent | Role | Focus |
|---|---|---|
| `fastapi-backend` | Senior Backend Dev | API Endpoints, Pydantic, ORM, Swagger |
| `fastapi-tester` | QA Engineer | Pytest, Integration Testing, Coverage |

## Included Skills

| Skill | Purpose |
|---|---|
| `project-context` | Shared environment, DB settings, architecture |
| `fastapi-standards` | PEP 8, FastAPI structure, security, error handling |
| `fastapi-testing` | Pytest fixtures, TestClient patterns, mocking |
| `fastapi-porm` | Pydantic v2 models, SQLAlchemy ORM patterns, migrations |

## Requirements

- Python 3.10+
- FastAPI with Pydantic v2
- SQLAlchemy (or your preferred ORM)
- Pytest with `httpx` for testing
- `pydantic-settings` for configuration management
