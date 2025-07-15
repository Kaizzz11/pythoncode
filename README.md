# Laravel App Production-Ready Setup

A full production-like setup for a Laravel application using Docker, Kubernetes (via Helm), and GitLab CI/CD pipelines for automation and deployment.

---

## 📦 Architecture

### Local Development
- Laravel + MongoDB + Elasticsearch in containers via **Docker Compose**.

### Production Architecture
- Laravel app containerized and deployed to **Kubernetes** using **Helm**.
- MongoDB and Elasticsearch are hosted externally (e.g., managed clusters or self-hosted).

### CI/CD Pipeline
- **GitLab CI/CD** pipeline handles:
  - Code testing
  - Docker image builds
  - Simulated Helm-based deployment

---

## 🌐 Environments

| Environment   | Description                                                  |
|---------------|--------------------------------------------------------------|
| Local         | Docker Compose setup for fast development                    |
| Development   | Simulated Kubernetes deployment with custom Helm values      |
| Staging       | Production-like setup used for testing before going live     |
| Production    | Fully simulated in CI/CD (no real infra required)            |

---

## 🔁 CI/CD Workflow

### 🔍 Stages Explained

- **Test**:  
  Runs unit/integration tests on every merge request to validate code stability.
  
- **Build**:  
  Builds and pushes Docker image after a successful merge.
  
- **Deploy**:  
  Simulates deploying the app to Kubernetes using Helm.

### ⚙️ Trigger Rules

- `test` stage runs on Merge Requests to `main` branch.
- Merge is blocked if tests fail.
- After merging to `main`, `build` and `deploy` stages run automatically.
- Docker images are pushed to DockerHub or simulated registry.
- Deployment is simulated to an EKS-like cluster using Helm.

---

## 🚀 Getting Started

### 1. Run Project Locally with Docker Compose

```bash
docker-compose up --build
