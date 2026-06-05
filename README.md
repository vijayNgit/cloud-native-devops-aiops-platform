# Cloud-Native DevOps & AIOps Platform on AWS EKS

## Overview

This repository contains my implementation of an end-to-end DevOps and AIOps platform deployed on AWS EKS.

The project deploys a 7-tier cloud-native microservices application on AWS EKS and demonstrates the complete lifecycle of modern platform engineering:

CI/CD → GitOps → Kubernetes → Observability → Centralized Logging → AIOps

The project demonstrates how modern cloud-native applications move from source code to production through automated CI/CD pipelines, GitOps workflows, observability tooling, centralized logging, and AI-assisted incident diagnosis.

The implementation was completed as a hands-on learning project under the guidance of Vishakha Sadwani. I deployed, configured, tested, troubleshot, and documented the complete workflow in my own AWS environment to gain practical experience with modern DevOps, Cloud, Platform Engineering, and AIOps practices.

---

## Architecture

```text
Developer
    │
    ▼
 GitHub Repository
    │
    ▼
 GitHub Actions CI/CD
    │
    ▼
 Docker Registry
    │
    ▼
 ArgoCD (GitOps)
    │
    ▼
 AWS EKS Cluster
    │
 ┌──┴─────────────┐
 ▼                ▼
Prometheus    Fluent Bit
 ▼                ▼
Grafana      CloudWatch
      \        /
       \      /
        ▼    ▼
     AWS Lambda
           │
           ▼
    AWS Bedrock Agent
           │
           ▼
      Kira Dashboard
           │
           ▼
 Root Cause Analysis
```

---

## Implementation Highlights

### 🚀 Automated Application Delivery

**Implemented** a CI/CD pipeline to automate application build and deployment workflows.

**Tech Stack:** GitHub Actions, Docker

**Outcome:** Enabled automated image creation and deployment workflows triggered by Git commits.

---

### ☸️ Deployed Cloud-Native Workloads

**Provisioned** and configured a Kubernetes environment for container orchestration.

**Tech Stack:** AWS EKS, Kubernetes, Docker

**Outcome:** Successfully deployed and managed microservices in a scalable cloud-native environment.

---

### 🔄 Adopted GitOps Practices

**Configured** GitOps-based deployment workflows to manage cluster state through Git.

**Tech Stack:** ArgoCD, Kustomize, Kubernetes

**Outcome:** Established version-controlled deployments and minimized configuration drift.

---

### 📊 Established Observability

**Integrated** monitoring and visualization capabilities for infrastructure and application health.

**Tech Stack:** Prometheus, Grafana

**Outcome:** Achieved real-time visibility into cluster performance, resource utilization, and service availability.

---

### 📝 Centralized Logging

**Implemented** centralized log collection and aggregation across Kubernetes workloads.

**Tech Stack:** Fluent Bit, AWS CloudWatch

**Outcome:** Enabled persistent, searchable logs enriched with Kubernetes metadata for faster troubleshooting.

---

### 🤖 Built an AI-Assisted Incident Analysis Workflow

**Integrated** AI-powered operational analysis using AWS Bedrock Agents and Lambda Action Groups.

**Tech Stack:** AWS Bedrock, AWS Lambda, CloudWatch, Python

**Outcome:** Enabled automated Root Cause Analysis (RCA) using live infrastructure logs and operational telemetry.

---

### 💬 Developed an Operations Dashboard

**Built** a conversational interface for infrastructure troubleshooting.

**Tech Stack:** Streamlit, Boto3, AWS Bedrock

**Outcome:** Enabled natural-language investigation of platform incidents and operational issues.

---

### 🔥 Validated Incident Response Workflows

**Simulated** service failures within the Kubernetes environment.

**Tech Stack:** Kubernetes, CloudWatch, Prometheus, AWS Bedrock

**Outcome:** Successfully identified failures and generated AI-assisted Root Cause Analysis using real operational data.

---

## End-to-End Workflow

### 1. Source Control

Developers push code changes to GitHub.

### 2. Continuous Integration

GitHub Actions automatically:

* Builds application artifacts
* Builds Docker images
* Pushes images to the container registry

### 3. GitOps Deployment

ArgoCD monitors Git repositories and synchronizes Kubernetes manifests with the EKS cluster.

### 4. Container Orchestration

AWS EKS manages:

* Deployments
* Services
* Scaling
* Rolling updates

### 5. Monitoring & Observability

Prometheus collects metrics from:

* Nodes
* Pods
* Services
* Kubernetes resources

Grafana visualizes operational health through dashboards.

### 6. Centralized Logging

Fluent Bit runs as a DaemonSet and:

* Collects container logs
* Enriches logs with Kubernetes metadata
* Ships logs to AWS CloudWatch

### 7. AIOps Workflow

When a user submits an operational question:

1. Kira (Streamlit) sends the request to AWS Bedrock Agent.
2. Bedrock determines what operational data is required.
3. Lambda Action Groups retrieve logs and metrics.
4. CloudWatch and monitoring data are analyzed.
5. Bedrock generates a Root Cause Analysis (RCA).
6. Results are returned through the dashboard.

---

## Why These Technologies?

### AWS EKS

Managed Kubernetes platform used to deploy and orchestrate microservices while reducing cluster management overhead.

### ArgoCD

Provides GitOps-based deployments where Git serves as the single source of truth for Kubernetes resources.

### Prometheus

Collects real-time infrastructure and application metrics for monitoring and alerting.

### Grafana

Visualizes metrics through dashboards that simplify operational analysis.

### Fluent Bit

Chosen for its lightweight footprint, Kubernetes-native design, metadata enrichment capabilities, and seamless integration with AWS CloudWatch.

### AWS CloudWatch

Provides centralized storage and search capabilities for operational logs.

### AWS Bedrock

Enables AI-powered reasoning and orchestration for operational investigations.

### AWS Lambda

Acts as the execution layer, allowing Bedrock Agents to retrieve live infrastructure data.

### Streamlit

Provides a lightweight interface for interacting with the AIOps workflow.

---

## Failure Simulation & Validation

To validate the AIOps workflow, a critical Kubernetes deployment was intentionally scaled to zero replicas.

The system successfully:

* Retrieved logs from CloudWatch
* Analyzed infrastructure telemetry
* Correlated service failures with unavailable pods
* Generated an automated Root Cause Analysis (RCA)

This demonstrated how observability and AI can be combined to assist operational troubleshooting.

---

## Repository Structure

```text
.
├── docs/
│   ├── part1-system-design.md
│   ├── part2-workflow.md
│   └── claude-setup.md
│
├── projects/
│   ├── boutique-microservices/
│   ├── Infrastructure/
│   └── aiops-assistant/
│
├── gitops/
│   ├── argo-cd.yml
│   ├── kustomization.yml
│   └── k8s/
│
├── docs/screenshots/
│
└── .github/
    └── workflows/
```

---

## Screenshots

Add screenshots demonstrating:

* AWS EKS Cluster
* GitHub Actions Pipeline Success
* ArgoCD Synchronization
* Kubernetes Workloads
* Prometheus Targets
* Grafana Dashboards
* CloudWatch Logs
* AWS Bedrock Agent Configuration
* Kira Dashboard
* Root Cause Analysis Output

---

## Technology Stack

| Category                | Technology                 |
| ----------------------- | -------------------------- |
| Cloud Platform          | AWS                        |
| Containerization        | Docker                     |
| Container Orchestration | Kubernetes (EKS)           |
| Infrastructure as Code  | Terraform                  |
| CI/CD                   | GitHub Actions             |
| GitOps                  | ArgoCD, Kustomize          |
| Monitoring              | Prometheus                 |
| Visualization           | Grafana                    |
| Logging                 | Fluent Bit, AWS CloudWatch |
| AIOps                   | AWS Bedrock Agents         |
| Serverless              | AWS Lambda                 |
| Frontend                | Streamlit                  |
| Programming Language    | Python                     |

---

## Key Learnings

Through this project, I gained hands-on experience with:

* Kubernetes administration and deployments
* Cloud-native application delivery
* GitOps workflows
* Infrastructure automation with Terraform
* Monitoring and observability practices
* Centralized logging architectures
* AWS cloud services integration
* AI-assisted incident investigation
* Platform Engineering fundamentals
* End-to-end DevOps lifecycle management

---

## Acknowledgements

This project was implemented as a hands-on learning project based on the DevOps + AIOps series created by Vishakha Sadwani.

The original series provided architectural guidance and learning resources. My focus was on deploying, configuring, testing, troubleshooting, documenting, and understanding the complete workflow while gaining practical experience with modern DevOps, Cloud, and AIOps technologies.
