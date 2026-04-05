# FastAPI Standards & Security

Comprehensive standards for secure, high-quality FastAPI development.

## 1. Security Checklist (Mandatory for every API)

- [ ] **Authentication**: Is the endpoint protected? (unless explicitly public).
- [ ] **Authorization**: Does the user have the required `scopes` or roles?
- [ ] **Input Validation**: Are all inputs validated via Pydantic (types, regex, constraints)?
- [ ] **SQL Injection**: Using ORM (SQLAlchemy/Tortoise) or prepared statements?
- [ ] **Data Exposure**: Does the `response_model` exclude sensitive fields (passwords, internal IDs)?
- [ ] **XSS/Injection**: Is user-generated content sanitized before storage or rendering?
- [ ] **Rate Limiting**: Is this endpoint susceptible to abuse? (e.g., login, search).
- [ ] **Error Details**: Are stack traces hidden from the user in production?

## 2. API Design Standards

- **Versioning**: All routes prefixed with `/api/v1/`.
- **Naming**: Use `kebab-case` for URLs (e.g., `/user-profiles/`) and `snake_case` for JSON keys.
- **Methods**: 
  - `GET`: Read-only, idempotent.
  - `POST`: Create resource.
  - `PUT`: Full update (replace).
  - `PATCH`: Partial update.
  - `DELETE`: Remove resource.
- **Status Codes**:
  - `200 OK`: Success (default).
  - `201 Created`: Success for POST.
  - `204 No Content`: Success for DELETE.
  - `400 Bad Request`: Validation or business logic error.
  - `401 Unauthorized`: Missing or invalid token.
  - `403 Forbidden`: Insufficient permissions.
  - `404 Not Found`: Resource non-existent.
- **Pagination**: Use `limit` and `offset` for list endpoints.

## 3. Code Standards (Clean Code)

- **Type Hinting**: 100% coverage for function signatures.
- **DOCSTRINGS**: Required for all public-facing routes and complex logic.
- **Dependency Injection**: Use `Depends()` for DB, Auth, and Services.
- **Pydantic v2**: Use `EmailStr`, `HttpUrl`, and `Field` for robust validation.
- **Logging**: Log significant events (errors, auth failures) using the standard library `logging`.
- **Linting**: Consistent formatting (handled by `black` or `ruff` if available).

## 4. Exception Handling Pattern

```python
from fastapi import HTTPException, status

def raise_unauthorized():
    raise HTTPException(
        status_code=status.HTTP_401_UNAUTHORIZED,
        detail="Could not validate credentials",
        headers={"WWW-Authenticate": "Bearer"},
    )
```
