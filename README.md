# health-monitor

Build a health monitoring service step by step. Each step applies concepts from the corresponding lesson in the [APIs & Async](https://dutchengineer.com/foundations/apis-async/) module.

## Setup

```bash
uv sync --all-extras
uv run pytest tests/ -v
```

## Run locally

```bash
uv run uvicorn health_monitor.app:app --reload
```

## Steps

| Step | Topic | Test file | Command |
|------|-------|-----------|---------|
| 1 | Build the API | `tests/test_step1_api.py` | `uv run pytest tests/test_step1_api.py` |
| 2 | Health Checks | `tests/test_step2_calls.py` | `uv run pytest tests/test_step2_calls.py` |
| 3 | Sequential Cost | `tests/test_step3_sequential.py` | `uv run pytest tests/test_step3_sequential.py` |
| 4 | Concurrent Checking | `tests/test_step4_concurrency.py` | `uv run pytest tests/test_step4_concurrency.py` |
| 5 | CPU Validation | `tests/test_step5_parallel.py` | `uv run pytest tests/test_step5_parallel.py` |
| 6 | Streaming Results | `tests/test_step6_streaming.py` | `uv run pytest tests/test_step6_streaming.py` |

## Workflow

1. Read the step instructions on the [project page](https://dutchengineer.com/foundations/apis-async/project-health-monitor/)
2. Implement the step
3. Run the tests for that step
4. Commit and push
5. CI runs all tests — green checks mean the step passes

## Project structure

```
src/health_monitor/
├── __init__.py
├── app.py           # FastAPI application (Steps 1, 3-4, 6)
├── checker.py       # Health check logic (Step 2)
├── models.py        # Pydantic models (Step 1)
└── validator.py     # CPU-intensive validation (Step 5)
locustfile.py        # Load testing (Step 6)
Dockerfile           # Container build (provided)
docker-compose.yml   # Multi-service setup (provided)
```

## Run with Docker

```bash
docker compose up --build
```

The API runs on port 8000. The Locust load testing UI runs on port 8089.
