# 🚀 FastAPI Comprehensive Cheatsheet

## 🔹 Install & Setup
```sh
# Install FastAPI and Uvicorn (ASGI server)
pip install fastapi uvicorn

# Run FastAPI app
uvicorn main:app --reload
```

## 🔹 Basic FastAPI Application
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, FastAPI!"}
```

## 🔹 Path Parameters
```python
@app.get("/users/{user_id}")
def get_user(user_id: int):
    return {"user_id": user_id}
```

## 🔹 Query Parameters
```python
@app.get("/items")
def get_items(skip: int = 0, limit: int = 10):
    return {"skip": skip, "limit": limit}
```

## 🔹 Request Body (Pydantic Models)
```python
from pydantic import BaseModel

class User(BaseModel):
    name: str
    age: int

@app.post("/users")
def create_user(user: User):
    return {"name": user.name, "age": user.age}
```

## 🔹 Form Data
```python
from fastapi import Form

@app.post("/login")
def login(username: str = Form(...), password: str = Form(...)):
    return {"username": username}
```

## 🔹 Handling File Uploads
```python
from fastapi import File, UploadFile

@app.post("/upload")
def upload_file(file: UploadFile = File(...)):
    return {"filename": file.filename}
```

## 🔹 Response Model
```python
class Item(BaseModel):
    name: str
    description: str
    price: float

@app.get("/items/{item_id}", response_model=Item)
def get_item(item_id: int):
    return {"name": "Example", "description": "A sample item", "price": 10.5}
```

## 🔹 Dependency Injection
```python
from fastapi import Depends

def get_db():
    db = {"db": "connected"}
    return db

@app.get("/db")
def read_db(db: dict = Depends(get_db)):
    return db
```

## 🔹 Background Tasks
```python
from fastapi import BackgroundTasks

def write_log(message: str):
    with open("log.txt", "a") as f:
        f.write(message + "\n")

@app.post("/log")
def log_message(message: str, background_tasks: BackgroundTasks):
    background_tasks.add_task(write_log, message)
    return {"message": "Logging started"}
```

## 🔹 Middleware
```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

## 🔹 Authentication with OAuth2
```python
from fastapi.security import OAuth2PasswordBearer

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

@app.get("/protected")
def protected_route(token: str = Depends(oauth2_scheme)):
    return {"token": token}
```

## 🔹 WebSockets
```python
from fastapi import WebSocket

@app.websocket("/ws")
async def websocket_endpoint(websocket: WebSocket):
    await websocket.accept()
    while True:
        data = await websocket.receive_text()
        await websocket.send_text(f"Message received: {data}")
```

## 🔹 Testing with Pytest
```python
from fastapi.testclient import TestClient

client = TestClient(app)

def test_read_root():
    response = client.get("/")
    assert response.status_code == 200
    assert response.json() == {"message": "Hello, FastAPI!"}
```

## 🔹 FastAPI Best Practices
- Use **Pydantic models** to validate request data.
- Implement **dependency injection** for modularity.
- Use **async/await** for non-blocking operations.
- Secure endpoints with **OAuth2 or JWT authentication**.
- Utilize **CORS middleware** for frontend-backend interaction.

---