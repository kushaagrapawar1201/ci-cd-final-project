# ci-cd-final-project

[![CI workflow](https://github.com/kushaagrapawar1201/ci-cd-final-project/actions/workflows/workflow.yml/badge.svg)](https://github.com/kushaagrapawar1201/ci-cd-final-project/actions/workflows/workflow.yml)

## Project Name
ci-cd-final-project

This repository contains the application and CI/CD pipelines developed as part of the **IBM DevOps and Software Engineering: Continuous Integration and Continuous Delivery (CI/CD)** course on Coursera.

## Project Details
- **Project Name:** ci-cd-final-project
- **Author:** Kushagra Pawar (`kushaagrapawar1201`)
- **Course:** Continuous Integration and Continuous Delivery (CI/CD) - IBM DevOps Professional Certificate
- **Stack:** Python 3.9, Flask, Gunicorn, Flake8, Nose, Docker, GitHub Actions, Tekton, Red Hat OpenShift

## Pipeline Architecture
1. **Continuous Integration (GitHub Actions):**
   - Automatically triggered on `push` and `pull_request` to the `main` branch.
   - Runs in containerized `python:3.9-slim` environment.
   - Installs dependencies from `requirements.txt`.
   - Runs code linting with `flake8`.
   - Executes automated unit tests with `nosetests` and generates test coverage metrics.

2. **Continuous Delivery (Tekton & OpenShift Pipelines):**
   - **`cleanup` Task:** Cleans workspace directory before building.
   - **`git-clone` Task:** Clones application source code from GitHub repository.
   - **`flake8` Lint Task:** Enforces code quality and syntax integrity.
   - **`nose` Test Task:** Runs automated unit tests inside Tekton workspace.
   - **`buildah` Task:** Builds container image and pushes to OpenShift internal image registry.
   - **`openshift-client` / `deploy` Task:** Deploys application onto Red Hat OpenShift cluster.

## Running Tests Locally
```bash
# Install dependencies
pip install -r requirements.txt

# Run linter
flake8 service --count --max-complexity=10 --max-line-length=127 --statistics

# Run unit tests
nosetests -v --with-spec --spec-color --with-coverage --cover-package=service
```
