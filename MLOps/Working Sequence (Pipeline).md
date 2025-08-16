# General working sequence (pipeline) for MLOps projects — short & actionable

# 1. Project bootstrap (once)
**Goal:** reproducible dev environment and repo layout.  
**Artifacts:** `.venv/` or Conda env, `requirements*.txt` / `pyproject.toml`, repo skeleton.

- Init structure: `mkdir -p data/{raw,processed,external} models app notebooks src tests`
- Create env & deps:
  - `python3 -m venv .venv && source .venv/bin/activate`
  - `pip install pip-tools pytest black`
  - `pip-compile requirements.in && pip-sync requirements.txt`
- Recommended files: `configs/`, `Makefile`, `Dockerfile`, `infra/`
- Acceptance: `make setup` installs deps and `python -c "import src; print('ok')"` returns `ok`.

---

# 2. Data ingestion & storage
**Goal:** reliably capture raw data and keep immutable source-of-truth.  
**Artifacts:** `data/raw/...`, ingestion script, manifest/checksums.

- Policy: **never** overwrite `data/raw/`.
- Script: `src/ingest.py` — example:
  - `python -m src.ingest --src s3://... --out data/raw/`
- Checkpoint: `data/processed/dataset.parquet` or `data/processed/{train,val,test}.parquet`
- Acceptance: manifest/checksum updated and basic schema validation passes.

---

# 3. Exploratory Data Analysis (EDA)
**Goal:** discover distributions, missingness, target balance and log preprocessing decisions.  
**Artifacts:** `notebooks/eda.ipynb`, `EDA_DECISIONS.md`.

- Focus: distributions, missingness, class balance, correlations, feature types.
- Deliverable: short `EDA_DECISIONS.md` listing "drop/keep", impute rules, derived features.
- Acceptance: documented decisions + reproducible notebook.

---

# 4. Preprocessing & feature engineering
**Goal:** deterministic, testable transforms (raw → model-ready).  
**Artifacts:** `src/preprocess.py`, `src/features.py`, `data/processed/{train,val,test}.parquet`.

- Implement pure functions, pipelineable steps (clean → impute → encode → scale → features).
- Run: `python -m src.preprocess --in data/raw/ --out data/processed/`
- Tests: `tests/test_preprocess.py` (shapes, sample outputs).
- Acceptance: deterministic outputs and unit-tested transforms.

---

# 5. Experiments: training & evaluation
**Goal:** train models, track experiments, select candidates.  
**Artifacts:** `src/train.py`, MLflow/W&B experiment logs, `models/vX.Y/`.

- CLI example:
  - `python -m src.train --config configs/default.yml --out models/v0.1`
- Track params, metrics, artifacts; set random seed for reproducibility.
- Smoke run for CI: `python -m src.train --quick`
- Acceptance: best model meets threshold or documented tradeoff.

---

# 6. Model validation & testing
**Goal:** verify correctness, robustness, and reproducibility.  
**Artifacts:** `tests/test_model_integration.py`, `tests/test_prediction_contracts.py`.

- Unit tests: shapes, dtypes, deterministic outputs.
- Integration: load `models/vX.Y/model.pkl` and run sample predictions.
- Optional: calibration, fairness, and distribution-shift checks.
- Acceptance: CI passes all tests; model loads and predicts as expected.

---

# 7. Packaging & local demo
**Goal:** package model for local demo and QA.  
**Artifacts:** `app/` (Gradio or FastAPI), `app/requirements.txt`, demo Dockerfile.

- Minimal demo: `app/app.py` loads model and exposes `/predict`.
- Local run: `python app/app.py` or `uvicorn app.main:app --reload`
- Quick share (Gradio): `demo.launch(share=True)`
- Acceptance: demo runs locally and returns valid predictions.

---

# 8. CI / automation
**Goal:** automated checks for PRs and main branch.  
**Artifacts:** `.github/workflows/ci.yml`, `Makefile` targets.

- CI tasks: install deps, `pytest -q`, lint/format (black/ruff), optional smoke training or model load test.
- Acceptance: PRs must pass CI before merging.

---

# 9. Deployment (staging → production)
**Goal:** reliable path to expose models (API or hosted demo).  
**Artifacts:** Docker image, deploy configs, infra-as-code, HF Space repo for demos.

- Options:
  - Demo: Hugging Face Space (push `app/` + `requirements.txt`)
  - Production API: FastAPI + Docker → Cloud Run / ECS / Render / KFServing / BentoML
- Example: `docker build -t myapp:staging . && docker push ...`
- Acceptance: endpoint responds within SLA and returns expected predictions.

---

# 10. Monitoring, observability & feedback loop
**Goal:** detect drift and monitor production model health.  
**Artifacts:** dashboards, alerting rules, retraining triggers.

- Monitor: latency, error rates, prediction distributions, label feedback, key metrics.
- Tools: Prometheus/Grafana, Sentry, Evidently/WhyLabs, MLflow.
- Retrain: define thresholds to trigger retraining or human review.
- Acceptance: alerts and periodic health reports exist.

---

# 11. Versioning, lineage & governance
**Goal:** traceability of data → model → prediction.  
**Artifacts:** `models/v*`, data manifests, `MODEL_CARD.md`, changelog.

- Version data snapshots, model artifacts, and configs.
- Produce `MODEL_CARD.md` with use-cases, limits, metrics, fairness notes.
- Secrets in a secret manager (not in repo).
- Acceptance: reproduce model from commit hash + data snapshot + config.

---

# 12. Reproducibility & infra
**Goal:** reproducible experiments across machines.  
**Artifacts:** `Dockerfile`, `docker-compose.yml`, pinned deps, config files.

- Use seeds, pinned deps, containerized jobs, and saved dataset hashes.
- Acceptance: `docker build && docker run` reproduces expected behavior.

---

# 13. Team & documentation
**Goal:** maintainability and easy onboarding.  
**Artifacts:** `CONTRIBUTING.md`, `README.md`, `ONBOARDING.md`, architecture diagram.

- Document where data lives, run instructions, outputs, and contacts.
- Keep `EDA_DECISIONS.md`, `MODEL_CARD.md`, and `CHANGELOG.md` updated.
- Acceptance: new teammate runs `make setup && make smoke` and gets expected outputs.

---

# Quick checklist / common commands
- Setup: `make setup` or `python -m venv .venv && pip-sync requirements.txt`
- Ingest: `python -m src.ingest --out data/raw/`
- Preprocess: `python -m src.preprocess --in data/raw/ --out data/processed/`
- Train: `python -m src.train --config configs/default.yml --out models/v0.1`
- Test: `pytest -q`
- Demo: `python app/app.py`
- Deploy: `docker build -t myapp:latest . && docker push ...`

---

# Final tips
- Keep transforms deterministic and unit-tested.  
- Prefer parquet for processed data.  
- Log everything (params, metrics, artifacts). MLflow or W&B are low friction.  
- Start simple: baseline + clear metrics before complexity.  
- Automate the smallest reproducible pipeline first (ingest → preprocess → train → serve).  
- Add governance and monitoring early enough to capture drift and feedback.
