# DevOps Capstone Project

![Build Status](https://github.com/DragonKzWy/devops-capstone-project/actions/workflows/ci-build.yaml/badge.svg)

## Overview

This repository contains the **Capstone Project** for the **IBM Applied DevOps Engineering Professional Certificate**.

The objective of this project is to design, build, test, and deliver a **cloud-native RESTful microservice** by applying **Agile planning**, **Test-Driven Development (TDD)**, **Continuous Integration (CI)**, and **DevOps best practices**.

The microservice implemented is an **Account Service**, designed for managing customer accounts in an e-commerce platform.

## Account Service

The Account Service is a RESTful microservice built with **Python Flask** that manages the complete lifecycle of customer accounts.

### Features

- Create customer accounts
- Read account details
- Update existing accounts
- Delete accounts
- List all accounts
- Health check endpoint

The service follows REST principles and uses JSON for request and response payloads.

## REST API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET    | `/health` | Health check |
| GET    | `/` | Service metadata |
| POST   | `/accounts` | Create a new account |
| GET    | `/accounts` | List all accounts |
| GET    | `/accounts/{id}` | Read an account |
| PUT    | `/accounts/{id}` | Update an account |
| DELETE | `/accounts/{id}` | Delete an account |

## Technology Stack

- Python 3.9
- Flask
- PostgreSQL
- Docker
- GitHub Actions
- Nose (unit testing)
- Flake8 (linting)

## Development Practices

This project applies modern DevOps and software engineering practices.

### Agile Planning

- Product Backlog and Sprint Backlogs managed using a Kanban board
- User stories defined with acceptance criteria
- Sprint-based development workflow

### Test-Driven Development (TDD)

- Unit tests written before implementation
- Full CRUD and list functionality covered by tests
- Minimum of **95% code coverage** enforced

### Continuous Integration (CI)

- Implemented using **GitHub Actions**
- Automatically triggered on every push and pull request to the `main` branch
- CI pipeline includes:
  - Dependency installation
  - Code linting with Flake8
  - Unit tests with Nose
  - Code coverage reporting
- PostgreSQL database provided via Docker service during CI execution

## CI Workflow

The Continuous Integration pipeline is defined in:

`.github/workflows/ci-build.yaml`

The workflow provisions:
- Python 3.9 execution environment
- PostgreSQL service using `postgres:alpine`
- Automated linting and testing
- Build status badge displayed in this README

## Running the Project Locally

### Prerequisites

- Python 3.9+
- Docker
- PostgreSQL

### Setup

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### Run Unit Tests

```bash
nosetests
```

or

```bash
make test
```

### Run Linting

```bash
make lint
```

## Project Structure

```
devops-capstone-project/
├── service/
│   ├── routes.py
│   ├── models.py
│   ├── config.py
│   └── common/
├── tests/
│   ├── test_routes.py
│   └── test_models.py
├── .github/
│   └── workflows/
│       └── ci-build.yaml
├── README.md
├── requirements.txt
├── setup.cfg
└── Makefile
```

## Project Status

- Agile Planning completed
- RESTful API implemented
- Unit tests implemented with high coverage
- Continuous Integration pipeline configured
- Automated linting and testing enabled
- CI build status badge active

## Author

Developed as part of the IBM Applied DevOps Engineering Professional Certificate on Coursera.

## License

This project is provided for educational purposes as part of the IBM DevOps curriculum.