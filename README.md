# Flask CI/CD Deployment Project

## Overview
This project demonstrates a complete DevOps workflow by building, containerizing, and deploying a simple Python Flask web application. The pipeline automates code testing, Docker image builds, and cloud deployments using GitHub Actions and Terraform on AWS.

## Features
- **Python Flask** web application serving a simple endpoint
- **Docker** containerization for portability
- **Automated CI/CD pipeline** with GitHub Actions
- **Continuous Integration:** Automated testing with pytest
- **Continuous Delivery:** Builds and pushes Docker images to Docker Hub
- **Infrastructure-as-Code:** Uses Terraform to provision AWS EC2 for deployment
- **Cloud Deployment:** Publicly accessible Flask app hosted on AWS EC2

## Technologies Used
- Python 3.9+
- Flask
- Docker
- Git/GitHub
- GitHub Actions
- Terraform
- AWS EC2

## Project Structure
```plain
your-repo/
├── app.py
├── requirements.txt
├── test_app.py
├── Dockerfile
├── .dockerignore
├── .github/
│   └── workflows/
│       └── cicd.yml
└── terraform/
    └── main.tf
```

## Getting Started

1. **Clone the Repository**
   ```shell
   git clone https://github.com/yourusername/your-repo-name.git
   ```
   
2. **Run Locally**
   ```shell
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   python app.py
   # Visit http://localhost:5000
   ```

3. **Run Tests Locally**
   ```shell
   pytest test_app.py
   ```

4. **Build Docker Image Locally**
   ```shell
   docker build -t my-flask-app .
   docker run -p 5000:5000 my-flask-app
   ```

5. **Automatic CI/CD**
   - Every git push triggers GitHub Actions to:
     - Run tests
     - Build and push the Docker image to Docker Hub
   - Secrets required: `DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN` (set in repo Settings > Actions).
 
6. **Deploy to AWS (via Terraform)**
   - Navigate to your Terraform folder and run:
     ```shell
     terraform init
     terraform apply -auto-approve
     ```
   - Find the EC2 public IP from Terraform output and visit `http://<public_ip>` in your browser.
 
## How to Use
- **Make changes to `app.py`** as needed, commit, and push. The pipeline rebuilds and redeploys automatically.
