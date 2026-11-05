# 🖨️ CampusPrint — Self-Service College Xerox Kiosk

**CampusPrint** is a self-service college printing solution designed to simplify document printing for students. The project demonstrates how a modern web application can be containerized, deployed, scaled, monitored, and continuously updated using cloud-native DevOps technologies.

The project combines application development with AWS, Docker, Kubernetes, CI/CD automation, and monitoring to demonstrate an end-to-end cloud deployment workflow.

---

## 🚀 Project Overview

CampusPrint is designed to provide a convenient digital printing experience while demonstrating a production-oriented deployment architecture.

### Key Highlights

- Web application built with TypeScript.
- Containerized application using Docker.
- Automated CI/CD pipeline using GitHub Actions.
- Docker image publishing to Docker Hub.
- Application deployment on Amazon EKS.
- Kubernetes Horizontal Pod Autoscaler (HPA) for workload scaling.
- Prometheus and Grafana for monitoring and visualization.
- Automated image update and deployment workflow using an in-cluster image updater.

---

## 🏗️ Architecture

```text
              Developer
                  |
                  v
             GitHub Repo
                  |
                  v
          GitHub Actions CI/CD
                  |
          +-------+--------+
          |                |
       Install          Build & Test
       Dependencies       |
                          v
                    Docker Build
                          |
                          v
                    Docker Hub
                          |
                          v
                In-Cluster Image Updater
                          |
                          v
                    Amazon EKS
                          |
                  Kubernetes Deployment
                          |
                    CampusPrint App
                          |
                  Kubernetes Service
                          |
                       Users

       Monitoring: Prometheus + Grafana
       Scaling: Kubernetes HPA
```

---

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Frontend / Application | TypeScript, Bun |
| Containerization | Docker |
| Container Registry | Docker Hub |
| CI/CD | GitHub Actions |
| Cloud Platform | AWS |
| Container Orchestration | Amazon EKS, Kubernetes |
| Deployment Automation | In-cluster image updater |
| Monitoring | Prometheus |
| Visualization | Grafana |
| Infrastructure | AWS cloud infrastructure |

---

## ⚙️ CI/CD Workflow

The project uses GitHub Actions to automate application validation and Docker image publishing.

### Workflow

1. Developer pushes code to the `main` branch.
2. GitHub Actions triggers the CI pipeline.
3. Repository is checked out.
4. Bun dependencies are installed.
5. TypeScript lint/check is executed.
6. Frontend production build is generated.
7. Docker image build is validated.
8. The publish job builds and pushes the image to Docker Hub.
9. Images are published with two tags:
   - `latest`
   - Git commit SHA
10. The in-cluster image updater detects the published image update and triggers the Kubernetes deployment update.

### Docker Image

```text
makdev85/campusprint
```

Docker Hub: https://hub.docker.com/r/makdev85/campusprint

---

## ☁️ AWS & Kubernetes Deployment

The application is deployed on **Amazon Elastic Kubernetes Service (EKS)**.

### Kubernetes Components

- **Deployment:** Manages CampusPrint application pods.
- **Pods:** Run the containerized application.
- **Service:** Exposes the application through Kubernetes networking.
- **HPA:** Automatically adjusts the number of application replicas based on CPU utilization.
- **Image updater:** Detects new container images and automates application updates.

### Scaling

The application uses Kubernetes Horizontal Pod Autoscaler (HPA).

Configured scaling:
- Minimum replicas: 2
- Maximum replicas: 5
- Target CPU utilization: 70%

This allows Kubernetes to scale the application according to workload demand.

---

## 📊 Monitoring & Observability

The project uses Prometheus and Grafana to monitor the Kubernetes environment.

### Prometheus
- Collects metrics from the Kubernetes environment.
- Supports monitoring of cluster and application workloads.
- Provides metrics for monitoring resource utilization.

### Grafana
- Visualizes monitoring metrics through dashboards.
- Helps observe application and cluster performance.
- Provides visibility into resource utilization.

---

## 🔄 End-to-End Deployment Flow

```text
Code Change
    |
    v
Git Push to GitHub
    |
    v
GitHub Actions
    |
    v
Build & Test
    |
    v
Docker Image Build
    |
    v
Push Image to Docker Hub
    |
    v
Image Updater Detects New Version
    |
    v
Kubernetes Deployment Update
    |
    v
New Application Pods
    |
    v
CampusPrint Updated
```

---

## 💻 Local Development

### Prerequisites

- Git
- Bun
- Docker

### Clone the repository

```bash
git clone https://github.com/Makdev85/campusprint.git
cd campusprint
```

### Install dependencies

```bash
bun install --frozen-lockfile
```

### Run lint checks

```bash
bun run lint
```

### Build the application

```bash
bun run build
```

For local development, use the development script defined in `package.json`.

---

## 🐳 Docker

Build the Docker image:

```bash
docker build -t campusprint .
```

Run the container:

```bash
docker run -p 8080:80 campusprint
```

Open:

```text
http://localhost:8080
```

---

## 📁 Repository Structure

```text
campusprint/
│
├── .github/
│   └── workflows/
│       └── ci.yml
│
├── public/
├── src/
├── package.json
├── bun.lock
├── Dockerfile
└── README.md
```

*The structure above is a representative overview. Adjust it to match the actual repository.*

---

## 🎯 Learning Outcomes

Through this project, I gained practical experience with:

- Building and validating a TypeScript application.
- Containerizing applications using Docker.
- Creating automated CI/CD pipelines with GitHub Actions.
- Publishing Docker images to Docker Hub.
- Deploying containerized workloads on Amazon EKS.
- Managing Kubernetes Deployments, Services, and HPA.
- Implementing automated image-based deployment updates.
- Monitoring Kubernetes workloads using Prometheus and Grafana.
- Understanding cloud-native application deployment and operations.

---

## 👨‍💻 Author

**Mustafa**

B.Tech Computer Science Engineering

GitHub: [@Makdev85](https://github.com/Makdev85)

---

## ⭐ Support

If you find this project interesting, consider giving the repository a ⭐ on GitHub!

**CampusPrint — Making college printing simpler through cloud-native technology.**
