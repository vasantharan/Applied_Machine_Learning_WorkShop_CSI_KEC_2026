# Module 5 - Building a REST API for ML Model

## What is a REST API?

**REST API = Communication bridge**
- Connects ML model to outside world
- Allows applications to send data
- Returns prediction as response
- Works over HTTP
- Uses JSON format

**Simple Meaning:**
Client sends input → API sends data to model → Model predicts → API returns result

---

## Tech Stacks available for building API

- FastAPI
    - Modern framework
    - Very fast performance
    - Automatic API documentation
    - Easy validation
    - Production-ready
- Flask
    - Lightweight
    - Simple and beginner-friendly
    - Flexible
    - Good for small projects
- Streamlit
    - Used for ML web apps
    - UI-based deployment
    - Not mainly for REST APIs

**Today we learn:** FastAPI and Flask

---

## What is venv and why it is used?

**venv = Virtual Environment**

**Why we need it:**
1. Keeps project dependencies separate
2. Avoids package conflicts
3. Maintains clean environment
4. Different projects → different versions

- **Without venv:** Package version clashes may happen
- **With venv:** Each project has its own isolated environment

---

## requirements.txt

**requirements.txt = Dependency list**

**Example Content:**
- fastapi
- uvicorn
- scikit-learn
- pandas
- joblib

**Installation:** pip install -r requirements.txt

---

## Let's have a hands on
Refer the [`main.py`](./main.py) file