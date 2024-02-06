# Flask Application Deployment on AWS ECS with Fargate using CICD with Blue Green Deployment

This project demonstrates the deployment of a Flask web application, containerized with Docker, on AWS Elastic Container Service (ECS) using the Fargate launch type. The application is a simple web server with two pages, demonstrating basic navigation and functionality. A CI/CD pipeline is established to automate the deployment process with Blue Green Deployment

## Project Structure

- `app.py`: The Flask application file.
- `requirements.txt`: List of Python dependencies required by the application.
- `Dockerfile`: Instructions for Docker to build the application container.
- `/templates`: HTML templates for the web application.
- `README.md`: Documentation about the project (this file).
- `/stacks`: Folder contains three cloudformation templates
- `network-stack.yaml`: Template creates network related resources like vpc, subnets etc.
- `ecs-fargate-deployment.yml`: Template creates ECS Fargate application related resources
- `cicd-pipeline.yml`: Template creates the CI/CD Pipeline

## Running the Application Locally

To run the application locally, follow these steps:

1. **Set Up a Python Environment:**
   - It's recommended to use a virtual environment.
   - Run `python -m venv venv` to create a virtual environment.
   - Activate the environment with `source venv/bin/activate` (Linux/Mac) or `venv\Scripts\activate` (Windows).

2. **Install Dependencies:**
   - Run `pip install -r requirements.txt` to install required Python packages.

3. **Run the Flask Application:**
   - Execute `python app.py`.
   - The application will be accessible at `http://localhost:5000`.

## Containerizing the Application with Docker

1. **Build the Docker Image:**
   - Run `docker build -t my-flask-app .` to build the image.

2. **Run the Container:**
   - Use `docker run -p 5000:5000 my-flask-app` to run the container.
   - The application will be accessible at `http://localhost:5000`.

## Deployment on AWS ECS with Fargate

The application is deployed on AWS ECS using the Fargate launch type. The following AWS resources are used:

- AWS ECR (Elastic Container Registry) for storing the Docker image.
- AWS ECS (Elastic Container Service) for running the application.
- Fargate for serverless container execution.

### Steps for Deployment

1. **Push the Docker Image to ECR:**
   - Tag and push the built Docker image to your AWS ECR repository.

2. **Run the below Template to create network resources :**
   - /stacks/network-stack.yaml

3. **Run the below Template to deploy application ECS Fargate:**
   - ecs-fargate-deployment.yml

4. **Run the below Template to set up CI/CD Pipeline:**
   - ecs-fargate-deployment.yml


