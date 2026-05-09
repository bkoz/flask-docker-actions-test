# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A simple Flask web application containerized with Docker, used to test GitHub Actions workflows for building and testing Docker containers.

## Development Setup

**With Docker:**
```bash
docker build -t flask-app .
docker run -p 5000:5000 flask-app
```

**Without Docker:**
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```

## Common Commands

- **Build Docker image**: `docker build -t flask-app .`
- **Run container**: `docker run -p 5000:5000 flask-app`
- **Test locally**: `curl http://localhost:5000/` or `curl http://localhost:5000/health`
- **Stop container**: `docker stop <container-id>` (find ID with `docker ps`)

## Architecture

Simple Flask application with two endpoints:
- `/` - Main endpoint returning JSON welcome message
- `/health` - Health check endpoint for container monitoring

The GitHub Actions workflow (`.github/workflows/docker-build.yml`) automatically builds the Docker image, runs the container, and tests both endpoints on every push or PR to main.

## Important Notes

- The Flask app runs on port 5000 inside the container
- GitHub Actions workflow uses `ubuntu-latest` runner
- Docker Buildx is used for improved build performance
