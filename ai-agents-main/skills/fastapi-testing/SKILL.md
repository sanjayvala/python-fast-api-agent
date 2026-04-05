# FastAPI Testing Skills

Patterns and best practices for testing FastAPI applications with Pytest.

## Pytest Configuration

- **`conftest.py`**: Place shared fixtures here.
- **`pytest.ini`**: Set default CLI options (`--v`, `--cov`).
- **Async Tests**: Use `pytest-asyncio` for testing async routes.

## Essential Fixtures

### TestClient Fixture
```python
import pytest
from fastapi.testclient import TestClient
from app.main import app

@pytest.fixture
def client():
    with TestClient(app) as c:
        yield c
```

### Database Session Fixture
```python
@pytest.fixture
def db_session():
    # Setup test DB session
    # yield session
    # Rollback or cleanup
```

## Testing Strategies

### Integration Testing
- Use `TestClient` to send requests to your app.
- Check headers, status codes, and body content.

### Mocking Dependencies
- Use `app.dependency_overrides` to swap out production dependencies (e.g., mail services, external APIs) during tests.

### Handling Authentication
- Create a fixture that returns a valid JWT token.
- Pass the token in the `Authorization: Bearer <token>` header.

## Assertion Best Practices

- **Status Codes**: Always check these first.
- **Schema Validation**: Compare the response JSON against Pydantic models.
- **Side Effects**: If a POST request is made, verify the record exists in the (mock) database.

## Naming Conventions
- Test files: `test_*.py`
- Test functions: `test_*()`
- Fixtures: Descriptive names based on what they provide.
