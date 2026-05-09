# Flask Docker GitHub Actions Test

A simple Flask application containerized with Docker to test GitHub Actions workflows.

## Overview

This repository demonstrates:
- A basic Flask web application
- Dockerization of a Python application
- GitHub Actions workflow for building and testing Docker containers

## Application Endpoints

- `GET /` - Returns a welcome message
- `GET /health` - Health check endpoint

## Running Locally

### Using Pre-built Image from GHCR

```bash
docker pull ghcr.io/bkoz/flask-docker-actions-test:latest
docker run -p 5000:5000 ghcr.io/bkoz/flask-docker-actions-test:latest
```

### Building Locally

```bash
docker build -t flask-app .
docker run -p 5000:5000 flask-app
```

Visit http://localhost:5000 to see the application.

### Without Docker

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

## GitHub Actions

The repository includes a GitHub Actions workflow that:
1. Builds the Docker image
2. Runs the container
3. Tests the endpoints
4. Pushes to GitHub Container Registry (ghcr.io)
5. Displays the image size

The workflow runs on:
- Push to main branch (builds, tests, and pushes)
- Pull requests to main branch (builds and tests only)
- Manual trigger (workflow_dispatch)

## Container Registry

The Docker image is automatically published to:
`ghcr.io/bkoz/flask-docker-actions-test:latest`

**Multi-platform support:**
- linux/amd64 (x86_64)
- linux/arm64 (ARM64)

Tagged versions are also available based on branch names and commit SHAs.
