git fetch origin
git checkout 1-issue-4821-ci-cache-misses-on-integration-suite

# Agentdirpro
Agent work task 
name: integration-suite

on:
  push:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Set up Python 3.12
        uses: actions/setup-python@v5
        with:
          python-version: '3.12'

      - name: Restore venv cache
        id: cache-venv
        uses: actions/cache@v4
        with:
          path: .venv
          key: venv-ubuntu-312-${{ hashFiles('requirements-lock.txt') }}

      - name: Install dependencies
        if: steps.cache-venv.outputs.cache-hit != 'true'
        run: |
          python -m venv .venv
          .venv/bin/pip install -r requirements-lock.txt

      - name: Run integration tests
        run: .venv/bin/python -m pytest tests/ -q

