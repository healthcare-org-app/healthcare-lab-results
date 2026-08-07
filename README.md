# lab-results-service

lab-results-service — domain: lab

- **Port:** 8401
- **Language:** Python 3.11 + Flask
- **Database:** `lab` (Postgres, table `lab_results`)
- **Event bus:** Kafka

## API

| Method    | Path                       |
|-----------|----------------------------|
| GET       | `/api/lab_results/`          |
| POST      | `/api/lab_results/`          |
| GET       | `/api/lab_results/<id>`      |
| PUT/PATCH | `/api/lab_results/<id>`      |
| DELETE    | `/api/lab_results/<id>`      |
| GET       | `/health`                  |
| GET       | `/ready`                   |

## Events

**Publishes:** lab.result.available
**Subscribes:** (none)

## HTTP peer dependencies

- `lab-orders-service`
- `reference-ranges-service`
- `patients-service`
- `notifications-service`
- `audit-log-service`

## Local dev

```bash
pip install -e ../../libs/py-healthcare-common
pip install -r requirements.txt
cp .env.example .env
(cd ../../infra && docker compose up -d postgres kafka kafka-init)
python -m app.main
```

## Tests

```bash
pytest
```
