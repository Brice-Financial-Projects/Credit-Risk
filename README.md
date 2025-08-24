# Credit Risk Modeling

A pragmatic, production‑minded project for credit risk analytics focused on estimating probability of default (PD) from financial and market data. It includes data preparation, feature engineering, modeling, evaluation, and optional serving for real‑time or batch scoring.

## Features

- End‑to‑end workflow: data preparation → feature engineering → model training → evaluation → scoring
- Emphasis on transparent, statistically sound metrics and stability monitoring
- Reproducible experiments and configurable pipelines
- Ready for local development in a Python virtual environment

## Quickstart

Prerequisites:
- Python 3.12.x
- Git

Create and activate a virtual environment:
- macOS/Linux:
  - python3.12 -m venv .venv
  - source .venv/bin/activate
- Windows (PowerShell):
  - py -3.12 -m venv .venv
  - .venv\Scripts\Activate.ps1

Upgrade pip and install dependencies:
- pip install -U pip
- If you have a requirements file: pip install -r requirements.txt
- If the project is an installable package: pip install -e .

Optional tools you may want for notebooks:
- pip install jupyter ipython

## Usage

- Data exploration: launch Jupyter and open your notebooks
  - jupyter notebook
- Scripts and pipelines: run Python modules or scripts as needed
  - python path/to/script.py
  - python -m package.module
- Configuration: use environment variables or configuration files as appropriate for your setup.

Tip: Keep raw data immutable, and write intermediate/processed datasets to separate folders to ensure reproducibility.

## Testing

- Run the test suite:
  - pytest -q
- Generate coverage (if configured):
  - pytest -q --cov --cov-report=term-missing

## Code Quality

- Linting/formatting (if configured in your environment):
  - ruff check .
  - ruff format .
  - black .  # if you prefer Black
- Pre-commit hooks (if you use them):
  - pre-commit install
  - pre-commit run --all-files

## Project Conventions

- Use semantic commit messages (e.g., feat:, fix:, docs:, refactor:, test:)
- Prefer deterministic data splits for temporal modeling and firm‑aware validation
- Log experiment parameters and metrics for traceability
- Treat negative values in financial ratios (where valid) as informative signals rather than errors

## Troubleshooting

- If dependencies fail to build, ensure your Python version is 3.12 and your virtual environment is active.
- Clear caches when diagnosing issues:
  - find . -name "__pycache__" -type d -exec rm -rf {} +
  - rm -rf .pytest_cache .mypy_cache .ruff_cache

## Contributing

- Create a feature branch from main
- Add or update tests where applicable
- Ensure code is formatted and linted
- Open a pull request with a clear description and rationale

## License

This project is licensed under the terms specified in the repository’s LICENSE file.
