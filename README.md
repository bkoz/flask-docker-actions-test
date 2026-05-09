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

### With Docker

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
4. Displays the image size

The workflow runs on:
- Push to main branch
- Pull requests to main branch
- Manual trigger (workflow_dispatch)
