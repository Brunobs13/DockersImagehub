# Flask + Docker + GitHub Actions CI/CD Pipeline

Small production-style project that demonstrates a complete container workflow: build a Flask app, validate it with tests, and publish the Docker image to Docker Hub through GitHub Actions.

## Project Description
This repository is focused on CI/CD and container operations, not on ML modeling.

What it shows clearly:
- simple Flask API service
- automated test execution with `pytest`
- Docker image build using `DockerFile`
- GitHub Actions pipeline for build/test/publish
- Docker Hub push using repository secrets

## Stack
- Python 3.9+
- Flask
- Pytest
- Docker
- GitHub Actions
- Docker Hub

## Workflow (CI/CD)
Workflow file: `.github/workflows/cicd.yml`

Pipeline flow:
1. **dockerbuild**
   - checks if the Docker image builds correctly
2. **build-and-test**
   - installs Python dependencies
   - runs unit tests with pytest
3. **build-and-publish**
   - authenticates to Docker Hub with GitHub Secrets
   - builds and pushes the image tag `latest`

Required GitHub Secrets:
- `DOCKER_USERNAME`
- `DOCKER_PASSWORD`

## Repository Structure
```text
DockersImagehub/
├── .github/workflows/cicd.yml
├── DockerFile
├── app.py
├── test_app.py
├── requirements.txt
├── .gitignore
└── README.md
```

## Run Locally
### 1) Install dependencies
```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 2) Run tests
```bash
pytest -q
```

### 3) Run the app
```bash
python app.py
```

Open:
- `http://localhost:8000`

## Run with Docker
### Build
```bash
docker build -f DockerFile -t flasktest-app:local .
```

### Run
```bash
docker run --rm -p 8000:8000 flasktest-app:local
```

## Notes
- This repo intentionally keeps the app minimal so the focus stays on delivery workflow and container lifecycle.
- If needed, the same structure can be extended with staging/prod environments and versioned image tags.
