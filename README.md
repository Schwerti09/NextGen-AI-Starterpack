# Codex AUTOMIND

This repository contains a lightweight full-stack example for the **AUTOMIND Agency-in-a-Box** concept. It ships a SvelteKit frontend, a Node.js backend, simple AI stubs, and a small deployment helper.

## Structure

- `frontend/` – SvelteKit UI with a warp drive toggle.
- `backend/` – Express server exposing REST endpoints.
- `backend/` – Express server exposing REST endpoints and health checks, plus a dynamic UI generator.
- `ai_core/` – `NeuroProcessor` stub handling basic requests.
- `self_healing/` – Python monitor that illustrates an auto repair flow.
- self-healing logs are forwarded to Elasticsearch for monitoring.
- `profit_engine/` – Example Stripe integration with a TensorFlow pricing model.
- `security/` – QuantumGuard encryption utilities (keys loaded from Vault).
- `core/` – Configuration management.
- `deploy/` – `god_mode.sh` starts Docker containers.
- `integration/` – Simple event bus for module coordination.
- Additional modules in `supply_chain/`, `legal/`, `erp/`, and others illustrate
  optional enterprise features.
- `docker-compose.yml` – Development orchestration file.

## Getting Started

1. Install Docker and `docker-compose`.
2. Run the deployment script:
   ```bash
   bash deploy/god_mode.sh
   ```
3. Or run locally with Node:
   ```bash
   bash setup.sh  # installs Node and Python deps
   npm start
   ```
4. Copy `.env.example` to `.env` and add your secrets.
5. Copy `quantum_config.example.json` to `quantum_config.json` if you need to
   adjust settings. By default the backend listens on `8080` and the Svelte dev
   server on `7777`.
   Docker Compose reads these files automatically via `env_file`.

6. Access the frontend at [http://localhost:7777](http://localhost:7777).

## Running Tests

Execute the test suites to verify that all agents and the backend operate
correctly:

```bash
npm test
pytest -q
```

Before running tests for the first time, make sure dependencies are installed
via `setup.sh`.

Unit tests cover each agent and integration tests verify `/api/neuro-request`,
`/api/generate-ui`, and the `/api/health` endpoint. A new example profit engine
test is included.

An OpenAPI definition (`openapi.yaml`) documents all REST endpoints with
examples, including the new `/api/health` and `/api/explain` routes.

Several helper scripts like `install_future_tech.sh` demonstrate how optional
libraries could be installed for the advanced modules.

This is a proof of concept. See `AGENTS.md` for module details and integration notes.
