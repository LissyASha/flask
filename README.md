# Flask Sample App with Tests

This is a simple Flask web application with unit tests. The application provides a basic REST API for managing a list of items. It serves as a starting point for learning how to create a Flask application and write tests for it.

## Project Structure

The project is organized as follows:

- `app/`: Contains the Flask application and routes.
- `tests/`: Houses unit tests for the application.
- `run.py`: A script to run the Flask application.

# 🚀 CI/CD Pipelines for Flask Application

This repository demonstrates how to set up **CI/CD pipelines** for a simple Python Flask application using:

1. **Jenkins Pipeline**
2. **GitHub Actions Workflow**

---

## 📌 Part 1: Jenkins CI/CD Pipeline

### 🎯 Objective
Set up a Jenkins pipeline that automates the **build → test → deploy(Staging)** process for a Flask web application.

---
## Table of Contents

- [Project Setup](#project-setup)
- [Requirements](#requirements)
- [Jenkins CI/CD Pipeline](#jenkins-cicd-pipeline)
- [Testing the Application](#testing-the-application)
- [Deployment](#deployment)
- [Contact](#contact)

---

## Project Setup

1. Clone the repository:

```bash
git clone https://github.com/LissyASha/flask.git
cd flask

2. Requirements
   Python 3.10+
   Flask
   Gunicorn
   pytest
   Flask-Testing
3. Jenkins CI/CD Pipeline

   Jenkinsfile Overview
      ->Build Stage: Installs Python dependencies.
      ->Test Stage: Runs unit tests using pytest.
      ->Deploy Stage: Deploys Flask app using Gunicorn.
      ->Post Section: Sends email notifications on success/failure.

   Steps to Configure Jenkins:
      ->Create a new Pipeline Job in Jenkins.
      ->Configure Pipeline from SCM pointing to this repository.
      ->Enable GitHub hook trigger for GITScm polling.
      ->Add Jenkinsfile in the repo root.
      ->Update email settings in Jenkins:
         Manage Jenkins → Configure System → E-mail Notification
         Use your SMTP server and credentials.

<img width="1342" height="685" alt="image" src="https://github.com/user-attachments/assets/cf7cb9e9-bcb0-4b8b-84ed-9aad94fe0d55" />
