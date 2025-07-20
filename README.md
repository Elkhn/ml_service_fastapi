Model Service Api
Example The ML service is a web application that provides an API for interacting with a machine learning model. It allows users to send queries with prediction data and get results back.
Startup logic:
When launched, the application initializes FastAPI, which handles HTTP requests. The app also connects to the machine learning model and loads it into memory for use in making predictions.

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
    │   ├── routes              # Package with API route handlers
    │   │   ├── __init__.py     # Route package initializer
    │   │   ├── healthcheck.py  # Route for service health check
    │   │   ├── predict.py      # Route for model predictions
    │   │   └── router.py       # Main router
    ├── schemas                 # Package with data models
    │   ├── __init__.py         # Package initializer
    │   ├── healthcheck.py      # Schema for health check response
    │   └── requests.py         # Schema for API input requests
    └── services                # Package with business logic
        ├── __init__.py         # Package initializer
        ├── model.py            # Logic for working with the ML model
        └── utils.py            # Helper utilities


Getting started

docker-compose up --build


web-server on

http://0.0.0.0:8000


swagger ui on

http://0.0.0.0:8000/docs


For test

curl -X 'POST' \
  'http://0.0.0.0:7007/api/predict/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "text": "Привет, как дела? Что нового?"
}'