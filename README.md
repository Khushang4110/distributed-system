Below is an updated README file that reflects the latest instructions and commands. You can copy and paste this into your repository's README.md file.

---

```markdown
# distributed-system

## Project Overview

This project demonstrates a distributed system built using modern tools and technologies. The system consists of the following components:

- **Frontend**: A responsive web interface built with HTML, CSS, and JavaScript. It includes a form for user registration and performs client-side validation.
- **Backend:** A Python-based RESTful API built using Flask. It processes requests from the frontend and interacts with a MySQL database.
- **Database:** A MySQL database initialized with a predefined schema and sample data.
- **Containerization:** All components (frontend, backend, and database) are containerized using Docker.
- **Orchestration:** The application is deployed on a Kubernetes cluster using YAML configuration files.
- **Monitoring:** Basic monitoring is implemented using Prometheus and Grafana.
- **Version Control:** Git and GitHub are used to manage code changes and collaborate.

## Project Structure

```
distributed-system/
├── README.md
├── .gitignore
├── frontend/
│   ├── index.html
│   ├── styles.css
│   └── script.js
├── backend/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
├── database/
│   ├── schema.sql
│   ├── data.sql
│   └── Dockerfile
├── k8s/
│   ├── frontend-deployment.yaml
│   ├── frontend-service.yaml
│   ├── backend-deployment.yaml
│   ├── backend-service.yaml
│   ├── database-deployment.yaml
│   ├── database-service.yaml
│   └── ingress.yaml
└── monitoring/
    ├── prometheus-values.yaml
    ├── prometheus-configmap.yaml
    └── grafana-dashboard.json
```

## Getting Started

### Prerequisites

- **Git:** For version control.
- **Docker:** To build and run containers.
- **Kubernetes:** Use Minikube, Docker Desktop Kubernetes, or a cloud Kubernetes cluster.
- **kubectl:** Command-line tool for Kubernetes.
- **Python 3.9+:** For backend development.
- **Helm (Optional):** For deploying Prometheus and Grafana.

### Local Development

#### 1. Clone the Repository

```bash
git clone https://github.com/Khushang4110/distributed-system.git
cd distributed-system
```

#### 2. Build Docker Images

To build Docker images for each component of the project, follow these steps:

##### Frontend

```bash
cd frontend
docker build -t khushang4110/frontend:latest .
cd ..
```

##### Backend

```bash
cd backend
docker build -t khushang4110/backend:latest .
cd ..
```

##### Database

```bash
cd database
docker build -t khushang4110/database:latest .
cd ..
```

*Replace `khushang4110` with your Docker Hub username, "khushang4110 is my Docker Hub username".*

### Kubernetes Deployment

1. **Push Docker Images:**  
   Tag and push your images to your container registry:
   ```bash
   docker push khushang4110/frontend:latest
   docker push khushang4110/backend:latest
   docker push khushang4110/database:latest
   ```

2. **Deploy Kubernetes Resources:**  
   Apply the YAML files from the `k8s/` directory:
   ```bash
   kubectl apply -f k8s/database-deployment.yaml
   kubectl apply -f k8s/database-service.yaml
   kubectl apply -f k8s/backend-deployment.yaml
   kubectl apply -f k8s/backend-service.yaml
   kubectl apply -f k8s/frontend-deployment.yaml
   kubectl apply -f k8s/frontend-service.yaml
   kubectl apply -f k8s/ingress.yaml
   ```

3. **Verify Deployments:**  
   Run:
   ```bash
   kubectl get pods,services
   ```

### Monitoring Setup

Prometheus and Grafana are deployed via Helm.

#### Prometheus

- **Configuration:**  
  The custom Prometheus configuration is provided in `monitoring/prometheus-configmap.yaml` and referenced by `monitoring/prometheus-values.yaml`.

- **Installation:**  
  ```bash
  helm install my-prometheus prometheus-community/prometheus -f monitoring/prometheus-values.yaml
  ```
  This installs Prometheus and ensures the custom ConfigMap is used for scraping.

#### Grafana

- **Installation:**  
  ```bash
  helm repo add grafana https://grafana.github.io/helm-charts
  helm repo update
  helm install my-grafana grafana/grafana
  ```
- **Access Grafana:**  
  Port-forward to access Grafana:
  ```bash
  kubectl port-forward svc/my-grafana 3000:80
  ```
  Then open your browser at `http://localhost:3000` and import the dashboard from `monitoring/grafana-dashboard.json`.


## Repository URL

Access the full code and configuration files at:  
[https://github.com/Khushang4110/distributed-system](https://github.com/Khushang4110/distributed-system)

