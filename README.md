# Tekton CI/CD Pipeline Project

## Overview

This project leverages Tekton for CI/CD pipeline automation, focusing on deploying and testing a simple counter API service written in Python with Flask. The service exposes various REST API endpoints to manage counters, such as creating, reading, updating, and deleting counters. The Tekton pipeline automates tasks like testing, linting, and cleaning up the workspace, all integrated into a GitHub-based CI workflow.

### Components

- **Dockerfile**: Builds the Python environment and sets up the necessary dependencies for the API service.
- **API Service (`routes.py`)**: Implements RESTful endpoints for counter operations.
- **Tests (`test_routes.py`)**: Provides unit tests for the API using `unittest` and `nose`.
- **Tekton Tasks (`tasks.yml`)**: Defines steps for cleaning up the workspace and running tests.
- **Setup Script (`setup.sh`)**: Automates the setup of the project environment.
- **Tekton Pipeline (`workflow.yml`)**: Automates the CI/CD process with Tekton, triggering on push or pull requests.

## Requirements

- Tekton installed on your Kubernetes cluster.
- Python 3.9 or later.
- Docker to build and run the container.
- A Kubernetes environment to deploy the pipeline and test its steps.
- GitHub repository for version control.

## How to Run the Project

### 1. Clone the Repository

First, clone the repository to your local machine:

```bash
git clone https://github.com/your-username/tekton-ci-cd-project.git
cd tekton-ci-cd-project
