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

2. Set Up the Environment
Run the setup script to prepare your local development environment. This script will install Python 3.9, create a virtual environment, and install dependencies.

bash
Copy
bash setup.sh
This will perform the following actions:

Install Python 3.9 and set it as the default version.
Create a Python virtual environment.
Install project dependencies from requirements.txt.
Set up environment variables and configurations for the development environment.
3. Build the Docker Image
To build the Docker image for the API service, use the following command:

bash
Copy
docker build -t counter-api-service .
This will create a Docker container with the Python environment and the necessary dependencies for running the API.

4. Test the API Locally (Optional)
You can test the API locally by running the Flask application directly. First, run the following command to start the API service:

bash
Copy
docker run -p 8000:8000 counter-api-service
Visit http://localhost:8000 in your browser or use a tool like Postman to test the following endpoints:

GET /: Returns information about the service.
GET /health: Returns the health status of the service.
POST /counters/{name}: Creates a new counter.
GET /counters: Lists all counters.
GET /counters/{name}: Retrieves a specific counter.
PUT /counters/{name}: Updates a counter.
DELETE /counters/{name}: Deletes a counter.
5. Deploy the Pipeline on Tekton
To deploy the Tekton pipeline in your Kubernetes cluster, follow these steps:

5.1. Install Tekton (If not already installed)
Install Tekton in your Kubernetes cluster if it is not installed:

bash
Copy
kubectl apply -f https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
5.2. Apply Tekton Resources
Apply the Tekton task and pipeline definitions to your cluster:

bash
Copy
kubectl apply -f tasks.yml
kubectl apply -f workflow.yml
These resources define the tasks and the pipeline, including steps for:

Linting the code with flake8.
Running unit tests with nose.
Cleaning up the workspace after each run.
5.3. Set Up GitHub Repository (Optional)
If you want to trigger the pipeline on push or pull requests, you need to link your GitHub repository to your Kubernetes cluster. This step typically involves using webhooks or integrating with a CI/CD platform like GitHub Actions or Tekton.

6. Run the Pipeline
Once the Tekton resources are applied, you can trigger the pipeline by pushing changes to the main branch or by creating a pull request. The pipeline will automatically execute the following steps:

Lint the code with flake8.
Run unit tests using nose.
Clean up the workspace after each run.
You can check the status of the pipeline in your Tekton dashboard or use kubectl to view the logs:

bash
Copy
kubectl logs -f <pipeline-pod-name>
7. View the Results
Tekton Dashboard: You can monitor the status of the pipeline in the Tekton Dashboard.
GitHub Actions: If integrated, you can also monitor the status through GitHub Actions.
Logs: You can view the logs for any task failure by using the kubectl logs command.
8. Run Unit Tests Locally
To run the unit tests locally, follow these steps:

Install dependencies:
bash
Copy
python3 -m pip install --upgrade pip wheel
pip install -r requirements.txt
Run the tests using nose:
bash
Copy
nosetests -v --with-spec --spec-color --with-coverage --cover-package=service
9. Clean Up
To clean up the environment, you can run the following command:

bash
Copy
bash setup.sh cleanup
This will remove any temporary files and reset the environment.

Development
To contribute to this project:

Fork the repository.
Create a new branch for your changes.
Make your changes and commit them.
Create a pull request with a clear description of what has been done.
Conclusion
This project demonstrates a simple yet effective CI/CD pipeline using Tekton, Docker, and GitHub Actions for automating the deployment and testing of a Python-based REST API. By following this guide, you can easily set up a similar pipeline for your own applications and workflows.

markdown

### Key Changes:
- **Full Steps**: Added step-by-step instructions, including environment setup, Docker image build, pipeline deployment, and test execution.
- **Optional Testing**: Local testing steps for verifying the API.
- **Tekton Pipeline Deployment**: Clear instructions for deploying and running the Tekton pipeline.

