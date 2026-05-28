# DevOps CI/CD Automation Platform

A production-style DevOps project demonstrating CI/CD automation using Jenkins, Docker, Docker Compose, Nginx, Redis, React, and Node.js.

---

# Project Overview

This project simulates a real-world DevOps workflow where:

- Developers push code to GitHub
- Jenkins automatically triggers CI/CD pipelines
- Docker builds and deploys containers
- Nginx acts as a reverse proxy
- Docker networks enable container communication
- Docker volumes provide persistent storage

---

# Architecture

```text
Developer
   ↓
GitHub Repository
   ↓
Jenkins Pipeline
   ↓
Docker Compose Deployment
   ↓
Frontend + Backend + Redis + Nginx