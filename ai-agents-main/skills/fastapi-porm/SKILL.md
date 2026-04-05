# Pydantic & ORM (PORM) Skills

Patterns for data modeling, validation, and database interaction in FastAPI.

## Pydantic Modeling

- **Validation**: Use `Field` for descriptions, constraints, and examples.
- **Model Configuration**: Use `model_config = {"from_attributes": True}` (Pydantic v2) for ORM compatibility.
- **Base Models**: Create a shared `BaseModel` for common fields (ID, timestamps).

### Example Pydantic Model
```python
from pydantic import BaseModel, Field, EmailStr
from typing import Optional
from datetime import datetime

class UserBase(BaseModel):
    email: EmailStr
    full_name: Optional[str] = Field(None, max_length=100)

class UserCreate(UserBase):
    password: str = Field(..., min_length=8)

class User(UserBase):
    id: int
    is_active: bool
    created_at: datetime

    class Config:
        from_attributes = True
```

## ORM Patterns (SQLAlchemy)

- **Async Drivers**: Use `SQLAlchemy[asyncio]` for non-blocking I/O.
- **Relationship Mapping**: Use `relationship()` with correctly defined `back_populates`.
- **Database Session**: Inject `AsyncSession` via FastAPI `Depends`.

### Example ORM Model
```python
from sqlalchemy import Column, Integer, String, Boolean, DateTime
from sqlalchemy.sql import func
from .database import Base

class UserModel(Base):
    __tablename__ = "users"

    id = Column(Integer, primary_key=True, index=True)
    email = Column(String, unique=True, index=True, nullable=False)
    hashed_password = Column(String, nullable=False)
    is_active = Column(Boolean, default=True)
    created_at = Column(DateTime, server_default=func.now())
```

## Alembic Migrations

- **Revisioning**: Always use descriptive names for migration files.
- **Autogenerate**: Use `alembic revision --autogenerate` for schema changes.
- **Versioning**: Keep migrations version-controlled to ensure environmental consistency.
