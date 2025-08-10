# Node.js CI/CD Pipeline with Docker and GitHub Actions

## Overview
This project demonstrates setting up a Node.js application with automated testing, containerization, and a CI/CD pipeline for seamless deployment to staging and production environments.

## Features
- **Node.js Project Setup** – Initialized and structured for scalability.
- **Automated Testing** – Implemented using Jest and Supertest.
- **CI/CD Workflow** – Configured with GitHub Actions, triggered on:
  - Push events
  - Pull requests
  - New releases
- **Containerization** – Built and published Docker images to Docker Hub.
- **Deployment** – Automated deployment to:
  - **Staging** for testing
  - **Production** for live release

## Tech Stack
- Node.js
- Jest & Supertest
- Docker & Docker Hub
- GitHub Actions
- Google Cloud Run

## Deployment Flow
1. Push code or create a pull request → CI pipeline runs tests.
2. On release creation → Build and push Docker image.
3. Deploy to staging environment.
4. Promote to production environment after verification.

---
##  Continuous Integration, Delivery, and Deployment Explained

###  Continuous Integration (CI)  
- Developers create **feature branches** to work on new code.  
- CI workflows run **automated tests** on feature branches to ensure quality.  
- Once tests pass, feature branches are merged into the **main branch** (which can be risky).  
- This frequent merging and testing process is called **Continuous Integration**.

### Continuous Delivery (CD)  
- To reduce risk, changes are merged into a **staging branch** instead of directly into main.  
- The staging environment is used by QA for thorough testing before production.  
- This process of automatically preparing code for release is **Continuous Delivery**.

### Continuous Deployment  
- In **Continuous Deployment**, the release to the live production environment happens automatically without manual approval.  
- The pipeline triggers on events like:  
  - Pull request merged into main  
  - New release created  
  - Commit pushed directly to production branch (rare)  

---

### GitHub Actions CI Workflow Basics
- **on:** Event triggers (push, pull request, release)  
- **jobs:** Define isolated jobs running on VMs  
- **runs-on:** OS environment for jobs  
- **steps:** Checkout code, set environment variables, run tests, build and deploy  

### Google Cloud Service Account for Deployment
- Enables programmatic authentication with Google Cloud in CI/CD pipelines.  
- Uses a JSON key file containing service account credentials.  

### Why Trigger Deployment on Release Instead of Push?
Deploying on every push risks exposing unfinished features. By deploying only on a release:  
- Teams test and polish in staging.  
- Only stable, well-tested features reach production users.  
- Minimizes disruption and improves product quality.  