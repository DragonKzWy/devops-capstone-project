# DevOps Capstone Project

![Build Status](https://github.com/DragonKzWy/devops-capstone-project/actions/workflows/ci-build.yaml/badge.svg)

## Overview

This repository contains the **Capstone Project** for the **IBM Applied DevOps Engineering Professional Certificate**.

The objective of this project is to design, build, test, containerize, deploy, and automate the delivery of a **cloud-native RESTful microservice** using Agile Planning, Test-Driven Development (TDD), Continuous Integration (CI), Continuous Deployment (CD), Docker, Kubernetes/OpenShift, and Tekton Pipelines.

The microservice implemented is an **Account Service** for managing customer accounts in an e-commerce platform.

---

# Account Service

The Account Service is a RESTful microservice built with **Python Flask** that manages the complete lifecycle of customer accounts.

## Features

- Create customer accounts
- Read account details
- Update existing accounts
- Delete accounts
- List all accounts
- Health check endpoint
- Security headers (Flask-Talisman)
- CORS policies (Flask-CORS)

The service follows REST principles and uses JSON for request and response payloads.

---

# REST API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET    | `/health` | Health check |
| GET    | `/` | Service metadata |
| POST   | `/accounts` | Create a new account |
| GET    | `/accounts` | List all accounts |
| GET    | `/accounts/{id}` | Read an account |
| PUT    | `/accounts/{id}` | Update an account |
| DELETE | `/accounts/{id}` | Delete an account |

---

# Technology Stack

- Python 3.9
- Flask
- Flask-SQLAlchemy
- PostgreSQL
- Docker
- Kubernetes / OpenShift
- Tekton
- GitHub Actions
- Nose (unit testing)
- Flake8 (linting)
- Gunicorn (WSGI server)

---

# Development Practices

## Agile Planning

- Product Backlog and Sprint Backlogs managed using Kanban
- User stories defined with assumptions and acceptance criteria
- Sprint-based incremental development
- Technical debt properly labeled
- Security and CD pipeline added in later sprints

---

## Test-Driven Development (TDD)

- Tests written before implementation
- Full CRUD and LIST functionality covered
- Security headers tested
- CORS policy tested
- Error handlers tested
- Minimum **95% code coverage enforced**

Run tests:

```bash
nosetests
```

or

```bash
make test
```

---

## Continuous Integration (CI)

CI implemented using **GitHub Actions**.

Triggered automatically on:

- push to main
- pull request to main

Pipeline includes:

- Checkout
- Install dependencies
- Linting with Flake8
- Unit tests with Nose
- PostgreSQL service via Docker
- Coverage reporting

Workflow file:

```
.github/workflows/ci-build.yaml
```

---

# Security Implementation

## Security Headers

Implemented using **Flask-Talisman**.

The service returns:

- `X-Frame-Options: SAMEORIGIN`
- `X-Content-Type-Options: nosniff`
- `Content-Security-Policy`
- `Referrer-Policy`

HTTPS enforcement is disabled during testing.

---

## CORS Policy

Implemented using **Flask-CORS**.

Returns:

```
Access-Control-Allow-Origin: *
```

Verified via automated tests.

---

# Docker Containerization

The microservice is containerized using Docker.

## Dockerfile Characteristics

- Base image: `python:3.9-slim`
- Non-root execution user
- Dependencies installed via requirements.txt
- Gunicorn used as entrypoint
- Port 8080 exposed

Build image:

```bash
docker build -t accounts .
```

Run container:

```bash
docker run -p 8080:8080 accounts
```

Image pushed to:

```
us.icr.io/<NAMESPACE>/accounts:1
```

---

# Kubernetes Deployment (OpenShift)

The application is deployed to OpenShift using Kubernetes manifests.

## Components Created

- PostgreSQL (ephemeral template)
- Deployment (3 replicas)
- Service (ClusterIP)
- Route (edge termination)

## Deployment Files

```
deploy/deployment.yaml
deploy/service.yaml
```

The deployment:

- Uses environment variables from Kubernetes secrets
- Connects to PostgreSQL via service name `postgresql`
- Runs 3 replicas
- Exposes port 8080

---

# Continuous Deployment (CD)

A CD pipeline using **Tekton** was designed to:

- Clone repository
- Lint code
- Run tests
- Build Docker image
- Deploy to OpenShift

The pipeline automates Kubernetes deployment after validation.

---

# Running Locally

## Prerequisites

- Python 3.9+
- Docker
- PostgreSQL

## Setup

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Run Application

```bash
honcho start
```

or

```bash
gunicorn --bind=0.0.0.0:8080 service:app
```

---

# Project Structure

```
devops-capstone-project/
├── service/
│   ├── routes.py
│   ├── models.py
│   ├── config.py
│   ├── common/
│   └── __init__.py
├── tests/
│   ├── test_routes.py
│   └── test_models.py
├── deploy/
│   ├── deployment.yaml
│   └── service.yaml
├── .github/
│   └── workflows/
│       └── ci-build.yaml
├── Dockerfile
├── README.md
├── requirements.txt
├── setup.cfg
└── Makefile
```

---

# Sprint Summary

## Sprint 1
- CRUD implementation
- Unit tests
- Coverage > 95%

## Sprint 2
- GitHub Actions CI
- Security headers
- CORS policies

## Sprint 3
- Docker containerization
- Kubernetes deployment
- Tekton CD pipeline

---

# Project Status

- Agile Planning completed
- RESTful API implemented
- Unit tests with high coverage
- CI pipeline operational
- Security headers implemented
- CORS policy implemented
- Docker image built and pushed
- Kubernetes deployment running
- Route exposed on OpenShift
- CD pipeline designed

---

# Author

Developed as part of the **IBM Applied DevOps Engineering Professional Certificate** on Coursera.

---

# License

This project is provided for educational purposes as part of the IBM DevOps curriculum.
