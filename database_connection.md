# 📘 FastAPI Database Connection Optimization (MongoDB & PostgreSQL)

This markdown file outlines best practices for connecting FastAPI with MongoDB and PostgreSQL using efficient connection handling and pooling for high-performance applications.

---

## 🔗 PostgreSQL + FastAPI

### 🧱 Tech Stack

* FastAPI
* PostgreSQL
* SQLAlchemy (async)
* asyncpg

### 📦 Install Dependencies

```bash
pip install fastapi sqlalchemy[asyncio] asyncpg uvicorn
```

### ⚙️ Connection Setup (`db.py`)

```python
from sqlalchemy.ext.asyncio import create_async_engine, async_sessionmaker
from sqlalchemy.orm import declarative_base

DATABASE_URL = "postgresql+asyncpg://user:pass@localhost/db"

engine = create_async_engine(
    DATABASE_URL,
    pool_size=10,
    max_overflow=20,
    echo=True,
)

AsyncSessionLocal = async_sessionmaker(engine, expire_on_commit=False)
Base = declarative_base()
```

### 🔁 Dependency (`deps.py`)

```python
from db import AsyncSessionLocal

async def get_db():
    async with AsyncSessionLocal() as session:
        yield session
```

### 🚀 Usage in Routes

```python
@app.get("/users")
async def get_users(db: AsyncSession = Depends(get_db)):
    result = await db.execute(select(User))
    return result.scalars().all()
```

### 💡 Why It’s Fast

* Uses connection pooling
* Avoids creating a new connection per request
* Async engine allows non-blocking DB calls

---

## 🍃 MongoDB + FastAPI

### 🧱 Tech Stack

* FastAPI
* Motor (async MongoDB driver)

### 📦 Install Motor

```bash
pip install motor
```

### ⚙️ MongoDB Setup (`mongodb.py`)

```python
from motor.motor_asyncio import AsyncIOMotorClient

MONGO_URL = "mongodb://localhost:27017"
client = AsyncIOMotorClient(MONGO_URL)
db = client.mydb
```

### 🔁 Dependency Injection

```python
def get_db():
    return db
```

### 🚀 Usage in Routes

```python
@app.get("/items")
async def get_items(db=Depends(get_db)):
    items = await db.items.find().to_list(100)
    return items
```

### 💡 Performance Tips

* Motor handles pooling internally
* Avoids blocking with async MongoDB operations
* Use indexes on frequently queried fields

---

## 📈 Summary: Performance Tips

| Feature                | PostgreSQL                     | MongoDB                         |
| ---------------------- | ------------------------------ | ------------------------------- |
| Connection Pooling     | SQLAlchemy + asyncpg           | Handled internally by Motor     |
| Async Support          | `create_async_engine`          | `AsyncIOMotorClient`            |
| Dependency Handling    | `async with AsyncSessionLocal` | Simple `get_db()` function      |
| Indexing               | Yes (create on filter fields)  | Yes (especially for large docs) |
| Connection Reuse       | Yes                            | Yes                             |
| Avoid Per-Request Conn | Yes                            | Yes                             |

