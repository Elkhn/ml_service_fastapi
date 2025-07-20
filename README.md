# 🧠 Model Service API

This project is an example ML service — a web application that provides an API for interacting with a machine learning model.  
Users can send requests containing input data and receive model predictions in response.

---

## 🚀 Startup Logic

When launched:

- The application initializes a **FastAPI** server to handle HTTP requests.
- It connects to the **machine learning model**, loading it into memory for inference.
- Routes are defined for predictions and health checks.

---

## 📁 Project Structure

```
.
├── .docker
│   └── Dockerfile              # Dockerfile for building the container image
├── pyproject.toml              # Project dependencies and configuration
├── .env                        # Environment variables file
├── docker-compose.yml          # Docker container orchestration file
└── src
    ├── app.py                  # Main application file, initializes FastAPI
    ├── api                     # Package with API routes
    │   ├── __init__.py         # Package initializer
    │   ├── routes              # API route handlers
    │   │   ├── __init__.py
    │   │   ├── healthcheck.py  # Health check route
    │   │   ├── predict.py      # Prediction route
    │   │   └── router.py       # Main router
    ├── schemas                 # Pydantic models for validation
    │   ├── __init__.py
    │   ├── healthcheck.py      # Response schema for health check
    │   └── requests.py         # Input schema for prediction
    └── services
        ├── __init__.py
        ├── model.py            # ML model logic
        └── utils.py            # Utility functions
```

---

## 🛠️ Getting Started

```bash
docker-compose up --build
```

---

## 🌐 Web Interface

- **API Base URL:** [http://0.0.0.0:8000](http://0.0.0.0:8000)  
- **Swagger UI:** [http://0.0.0.0:8000/docs](http://0.0.0.0:8000/docs)

---

## 🧪 Sample Test (via `curl`)

```bash
curl -X 'POST' \
  'http://0.0.0.0:8000/api/predict/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "text": "Привет, как дела? Что нового?"
}'
```