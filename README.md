# Info

## Author Information

- **Name:** Juan Vicente Herrera Ruiz de Alejo
- **GitHub:** [@juanviz](https://github.com/juanviz)
- **Role:** Author and Maintainer
- **Affiliation:** ICAI

## License
This project is licensed under the MIT License - see the [MIT License](https://opensource.org/licenses/MIT) for details.
# Python App Deployment on Google Kubernetes Engine (GKE)

This repository contains a simple Python web application together with the configuration required to **build, containerize, and deploy it to Google Kubernetes Engine (GKE)** using **GitHub Actions**.

The project is designed as a **hands-on learning exercise** to demonstrate modern cloud-native development practices including containerization, Kubernetes deployments, and CI/CD automation.

---

# Overview

The repository demonstrates a typical **cloud-native deployment workflow**:

1. A developer pushes code to GitHub.
2. **GitHub Actions** builds a Docker image.
3. The image is pushed to **Google Artifact Registry**.
4. Kubernetes manifests are applied to a **Google Kubernetes Engine (GKE)** cluster.
5. The application is exposed through a Kubernetes **Service**.

This approach reflects how applications are deployed in modern DevOps and platform engineering environments.

---

# Repository Structure

```
.
├── app/
│   └── currency_converter.py              # Python application
├── requirements.txt         # Python dependencies
├── Dockerfile               # Container image definition
├── k8s/
│   ├── deployment.yaml      # Kubernetes Deployment
│   └── service.yaml         # Kubernetes Service
└── .github/
    └── workflows/
        └── deploy.yaml      # CI/CD pipeline
```

---

# Application

The application is a minimal Python web service that exposes a simple HTTP endpoint.


The application itself is intentionally simple because the **main focus of this repository is the deployment pipeline and infrastructure workflow**.

---

# Prerequisites

Before deploying the application you need:

### Google Cloud

* A **Google Cloud Project**
* **Google Kubernetes Engine (GKE)** enabled
* **Artifact Registry** enabled

### Required Tools

Install the following locally:

* `gcloud`
* `kubectl`
* `docker`

Authenticate with Google Cloud:

```bash
gcloud auth login
gcloud config set project YOUR_PROJECT_ID
```

---


# Configure GitHub Secrets

The GitHub Actions workflow requires the following repository secrets:

| Secret           | Description              |
| ---------------- | ------------------------ |
| `GCP_PROJECT_ID` | Google Cloud project ID  |
| `GCP_SA_KEY`     | Service account JSON key |
| `GKE_CLUSTER`    | Name of the GKE cluster  |
| `GKE_ZONE`       | Cluster zone             |

The service account should have permissions to:

* Push images to Artifact Registry
* Access the GKE cluster
* Deploy Kubernetes resources

---

# CI/CD Pipeline

The GitHub Actions workflow performs the following steps automatically:

1. Install Google Cloud SDK
2. Authenticate using the Service Account
3. Build the Docker container image
4. Push the image to Artifact Registry
5. Deploy the application to GKE using `kubectl`

The pipeline is triggered automatically on **push to the main branch**.

---


# Learning Objectives

This repository helps demonstrate:

* Containerization with **Docker**
* Kubernetes deployments
* CI/CD pipelines with **GitHub Actions**
* Deploying applications to **Google Kubernetes Engine**
* Basic cloud-native application lifecycle
