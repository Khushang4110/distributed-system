# distributed-system
## Project Overview

This project demonstrates a distributed system built using modern tools and technologies. The system consists of the following components:

- **Frontend:** A responsive web interface built with HTML, CSS, and JavaScript. It includes a form for user registration and performs client-side validation.
- **Backend:** A Python-based RESTful API built using Flask. It processes requests from the frontend and interacts with a MySQL database.
- **Database:** A MySQL database initialized with a predefined schema and sample data.
- **Containerization:** All components (frontend, backend, and database) are containerized using Docker.
- **Orchestration:** The application is deployed on a Kubernetes cluster using YAML configuration files.
- **Monitoring:** Basic monitoring is implemented using Prometheus and Grafana.
- **Version Control:** Git and GitHub are used to manage code changes and collaborate.

## Project Structure
distributed-system/
├── README.md
├── .gitignore
├── frontend/
├── backend/
├── database/
├── k8s/
└── monitoring/


## Getting Started

### Prerequisites

- **Git:** For version control.
- **Docker:** To build and run containers.
- **Kubernetes:** Use Minikube, Docker Desktop, or a cloud Kubernetes cluster.
- **kubectl:** Command-line tool for Kubernetes.
- **Python 3.9+:** For backend development.
- **Helm (Optional):** For deploying Prometheus and Grafana.

### Local Development

#### 1. Clone the Repository

```bash
git clone https://github.com/Khushang4110/distributed-system.git
cd distributed-system

## Build Docker Images

To build Docker images for each component of the project, follow these steps:

### Frontend

```bash
cd frontend
docker build -t Khushang4110/frontend:latest .
cd ..

cd backend
docker build -t Khushang4110/backend:latest .
cd ..

cd database
docker build -t Khushang4110/database:latest .
cd ..



