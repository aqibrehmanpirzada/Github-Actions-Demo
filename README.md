# GitHub Actions Demo: Python Calculator

This repository demonstrates the use of GitHub Actions for a Python project with a basic calculator implementation and associated tests.

## Files

- [calculator.py](calculator.py): Python script containing basic calculator functions.
- [test_calculator.py](test_calculator.py): Test script using `pytest` to test the calculator functions.

## Workflow

The repository includes a GitHub Actions workflow that runs tests using `pytest` whenever changes are pushed to the `main` branch.

### Workflow Configuration

The workflow is defined in the `.github/workflows/python-ci.yml` file.

```yaml
name: Python CI

on:
  push:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Code
      uses: actions/checkout@v2

    - name: Set up Python
      uses: actions/setup-python@v3
      with:
        python-version: 3.8

    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install pytest

    - name: Run tests
      run: pytest
