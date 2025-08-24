# Credit Risk Project Structure

credit-risk/
├─ README.md
├─ LICENSE
├─ .gitignore
├─ .env.example
├─ pyproject.toml                # package + dependencies (uv/poetry/pip-tools compatible)
├─ Makefile                      # single‑command workflows (fmt, lint, test, train, api, etc.)
├─ .pre-commit-config.yaml       # formatting/lint hooks (black, ruff, isort, yaml/md hooks)
├─ .flake8                       # optional linter config
├─ .ruff.toml                    # fast Python lints
├─ .editorconfig
├─ docker/
│  ├─ Dockerfile.api            # serve model with FastAPI/uvicorn
│  └─ Dockerfile.job            # batch jobs (train/eval) image
├─ k8s/                          # optional: manifests/helm for deployment
│  ├─ deployment.yaml
│  └─ service.yaml
├─ infra/                        # optional: IaC (Terraform) for buckets, registries, etc.
│  └─ terraform/
├─ .github/
│  └─ workflows/
│     ├─ ci.yml                 # lint + tests + type checks on PR
│     └─ publish.yml            # optional: publish package/docker on tag
├─ data/
│  ├─ README.md
│  ├─ raw/                      # immutable source files
│  │  └─ credit_risk_dataset.csv
│  ├─ interim/                  # lightly cleaned
│  ├─ processed/                # model‑ready parquet/csv
│  └─ external/                 # external merges (macro, industry, ratings)
├─ notebooks/
│  ├─ 01_eda.ipynb
│  ├─ 02_feature_engineering.ipynb
│  ├─ 03_modeling_PD.ipynb
│  └─ 99_scratchpad.ipynb
├─ reports/
│  ├─ figures/
│  └─ model_card.md             # transparent model card for PD model
├─ docs/
│  ├─ architecture.md
│  ├─ data_dictionary.md        # schema & ranges for WC/TA, RE/TA, …
│  ├─ risk_framework.md         # PD/LGD/EAD glossary (even if PD only now)
│  └─ api_contract.md           # request/response for scoring endpoints
├─ configs/
│  ├─ base.yaml                 # common config (paths, features, target, seed)
│  ├─ dev.yaml                  # dev overrides (small data, fast epochs)
│  └─ prod.yaml                 # prod overrides (full data, strict checks)
├─ src/
│  └─ credit_risk/
│     ├─ __init__.py
│     ├─ settings.py            # all settings via pydantic (env + yaml)
│     ├─ io/
│     │  ├─ load.py             # readers/writers (csv/parquet/s3)
│     │  └─ catalog.py          # central data path registry
│     ├─ data/
│     │  ├─ schema.py           # data contracts with pandera
│     │  ├─ split.py            # temporal split, firm‑aware CV
│     │  └─ preprocess.py       # cleaning, winsorize, scaling
│     ├─ features/
│     │  └─ build_features.py   # ratios, caps, industry standardization
│     ├─ modeling/
│     │  ├─ train.py            # trains PD model (logit/xgb) + calibration
│     │  ├─ evaluate.py         # AUC/PR, Brier, KS, PSI, calibration curves
│     │  ├─ backtest.py         # rolling/temporal backtests
│     │  ├─ thresholding.py     # cutoffs by cost matrix
│     │  └─ persistence.py      # save/load model+preproc with versioning
│     ├─ validation/
│     │  ├─ checks.py           # data drift, schema, leakage guards
│     │  └─ monitoring.py       # live PSI, score stability, default rate
│     ├─ pipelines/
│     │  ├─ build_dataset.py    # raw -> interim -> processed
│     │  ├─ train_pipeline.py   # end‑to‑end train (calls data→features→model)
│     │  └─ score_pipeline.py   # batch scoring job
│     ├─ service/
│     │  ├─ api.py              # FastAPI app for real‑time scoring
│     │  └─ schemas.py          # Pydantic request/response models
│     ├─ cli.py                 # Typer CLI: `credit-risk train`, `score`, `validate`
│     └─ utils/
│        ├─ logging.py          # structlog/logging config
│        ├─ metrics.py          # Gini, KS, lift tables, calibration
│        └─ seed.py             # reproducibility
├─ tests/
│  ├─ conftest.py
│  ├─ unit/
│  │  ├─ test_schema.py
│  │  ├─ test_features.py
│  │  └─ test_metrics.py
│  └─ integration/
│     ├─ test_train_pipeline.py
│     └─ test_api.py
└─ dvc.yaml                      # optional: data versioning pipeline (DVC)
