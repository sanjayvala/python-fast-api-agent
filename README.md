# Python FastAPI AI Agent System

A sophisticated collection of AI agents and specialized skills designed to accelerate Python FastAPI development with a security-first approach.

## Overview

This repository provides a modular, agent-driven development environment for building robust FastAPI backends. It integrates custom **Agents** (expert personas) and **Skills** (contextual knowledge) to automate repetitive tasks, enforce security standards, and maintain architectural consistency.

### Key Components

- **Agents**: Specialized AI personas like `fastapi-backend` (for feature development) and `fastapi-tester` (for QA and testing).
- **Skills**: Shared expert knowledge covering security standards, database patterns (SQLAlchemy/Pydantic), and project-specific contexts.
- **Workflow Automation**: Pre-defined workflows for API design, security auditing, and test generation.

---

## Configuration & Development Process

Follow these steps to configure your local environment and start developing with the AI agents.

### 1. Initial Setup

Clone this repository or copy the `ai-agents-main` directory into your project.

```bash
# Example: Copy agents and skills to your .claude directory
cp -r ai-agents-main/agents/ .claude/agents/
cp -r ai-agents-main/skills/ .claude/skills/
```

### 2. Configure Project Context

Navigate to `ai-agents-main/skills/project-context/SKILL.md` (or your local copy) and replace the placeholder values with your project's specific details:

- `{{API_BASE_URL}}`: Your local API endpoint (e.g., `http://localhost:8000`)
- `{{DB_HOST}}`, `{{DB_NAME}}`, `{{DB_USER}}`: Your database connection details.
- `{{CORS_ORIGINS}}`: Allowed origins for CORS configuration.

### 3. Development Workflow

The system is designed for a targetted development cycle:

1.  **Requirement Audit**: Describe your feature to the `fastapi-backend` agent.
2.  **Security Analysis**: The agent automatically performs a security check based on `fastapi-standards`.
3.  **Data Modeling**: Pydantic schemas and ORM models are generated following best practices.
4.  **Implementation**: FastAPI routes are implemented with full type hinting and async support.
5.  **Verification**: Use the `fastapi-tester` agent to generate and run integration tests.

### 4. Running Locally

Ensure you have Python 3.10+ installed and the required dependencies:

```bash
pip install fastapi sqlalchemy pydantic-settings pytest httpx
uvicorn app.main:app --reload
```

---

## Included Resources

| Service | Path | Description |
|---|---|---|
| **Agents** | [agents/](file:///Users/sanjay/Projects/Ai%20Agents/python-fast-api-agent/ai-agents-main/agents/) | Custom instruction files for AI personas. |
| **Skills** | [skills/](file:///Users/sanjay/Projects/Ai%20Agents/python-fast-api-agent/ai-agents-main/skills/) | Modular knowledge bases for security, testing, and ORM. |
| **Project Context** | [project-context](file:///Users/sanjay/Projects/Ai%20Agents/python-fast-api-agent/ai-agents-main/skills/project-context/SKILL.md) | Centralized configuration for the AI system. |
