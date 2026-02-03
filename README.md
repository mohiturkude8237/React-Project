# React-Project
This is React Project App.

# Weather App – CI/CD Deployment

A **React Weather Application** deployed using **Docker, Nginx, and Jenkins CI/CD**, following production-grade best practices.

---

## Table of Contents
1. [Project Overview](#project-overview)  
2. [Features](#features)  
3. [Tech Stack](#tech-stack)  
4. [Architecture](#architecture)  
5. [Getting Started](#getting-started)  
6. [CI/CD Pipeline](#cicd-pipeline)  
7. [Deployment](#deployment)  
8. [Future Enhancements](#future-enhancements)  
9. [Screenshots](#screenshots)

---

## Project Overview

This project demonstrates **end-to-end CI/CD** for a frontend React app:

- Multi-stage Docker builds for **production-ready static assets**
- **Nginx** for serving optimized static files
- **Jenkins pipeline** automating clone, build, and deployment
- **Docker Compose** for production container orchestration
- Optional integration for **HTTPS, zero-downtime deployment, and Docker registry push**

---

## Features

- ✅ React Weather App with responsive UI
- ✅ Production-grade static hosting with Nginx
- ✅ Automated build and deploy pipeline
- ✅ Smoke tests post-deployment
- ✅ Easy configuration via Docker Compose

---

## Tech Stack

- **Frontend:** React + Vite  
- **Web Server:** Nginx  
- **Containerization:** Docker & Docker Compose  
- **CI/CD:** Jenkins  
- **Cloud:** AWS EC2 (or any Linux server)  

---

## Architecture

  GitHub Repo
      |
      v
  Jenkins Pipeline
-------------------
| Clone Code      |
| Build Docker    |
| Deploy Compose  |
-------------------
      |
      v
Docker Container
+----------------+
| React App |
| /dist folder |
+----------------+
|
v
Nginx Server
|
v

Browser (HTTP/HTTPS)


---

## Getting Started

### Prerequisites
- Node.js (for local dev)
- Docker & Docker Compose
- Jenkins (optional, for CI/CD)
- EC2 instance (or any Linux server)

### Running Locally
```bash
git clone https://github.com/mohiturkude8237/Weather-App.git
cd Weather-App
npm install
npm run dev -- --host 0.0.0.0 --port 5173

Open http://localhost:5173

Building for Production (Docker)
docker build -t weather-app-prod .
docker run -d -p 80:80 weather-app-prod

Open http://localhost

Using Docker Compose
docker compose up -d --build

CI/CD Pipeline

Code Clone: Pull latest code from GitHub

Build Stage: Multi-stage Docker build

Deploy Stage: Stop old container, deploy new one via Docker Compose

Smoke Test: Simple curl to verify app availability

Jenkins Pipeline snippet:

pipeline {
  agent { label 'Vinod' }
  stages {
    stage('Clone') { git url: 'https://github.com/mohiturkude8237/Weather-App.git', branch: 'main' }
    stage('Build') { sh 'docker build -t weather-app-prod .' }
    stage('Deploy') { sh 'docker compose down || true; docker compose up -d' }
    stage('Test') { sh 'curl -f http://localhost' }
  }
}

