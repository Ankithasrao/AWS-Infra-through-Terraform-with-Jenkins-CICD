## AWS Infrastructure Provisioning using Terraform & Jenkins CI/CD

### Overview

This project automates AWS infrastructure provisioning using Terraform and Jenkins CI/CD. It integrates GitHub with Jenkins to automatically trigger pipeline execution whenever code changes are pushed to the repository.

The pipeline follows Infrastructure as Code (IaC) best practices by validating Terraform configurations, generating execution plans, and requiring manual approval before applying infrastructure changes.

Infrastructure state is securely stored in an Amazon S3 backend, enabling centralized state management and supporting collaboration.

## Architecture

```mermaid
flowchart TD
    A[Developer] -->|Git Push| B[GitHub Repository]
    B -->|Webhook Trigger| C[Jenkins Server on EC2]
    C --> D[Terraform CI/CD Pipeline]
    D --> E[Terraform Init]
    E --> F[Terraform Validate]
    F --> G[Terraform Format Check]
    G --> H[Terraform Plan]
    H --> I{Manual Approval}
    I -->|Approved| J[Terraform Apply]
    I -->|Rejected| K[Pipeline Aborted]
    J --> L[AWS EC2 Instance]
    C --> M[IAM Role]
    M -->|Secure AWS Authentication| J
    E --> N[S3 Remote State]
    H --> N
    J --> N
```

---

## 🚀 Project Objectives

* Automate AWS infrastructure provisioning using Terraform.
* Implement CI/CD automation using Jenkins.
* Integrate GitHub with Jenkins using webhooks.
* Implement Infrastructure as Code (IaC) best practices.
* Store Terraform state remotely using Amazon S3.
* Use IAM roles for secure AWS authentication.
* Implement manual approval before infrastructure deployment.
* Reduce manual infrastructure provisioning effort.

---

## Project Structure


```text
  AWS-Infra-through-Terraform-with-Jenkins-CICD/
│
├── Jenkinsfile
├── README.md
├── .gitignore
│
└── terraform/
    ├── main.tf
    ├── provider.tf
    ├── variables.tf
    ├── output.tf
    └── .terraform.lock.hcl
```

---

## 🛠️ Technologies Used

* AWS EC2 ---------- Hosting Jenkins and provisioning infrastructure
* AWS IAM ---------- Secure authentication and authorization
* AWS S3  ---------- Remote Terraform state storage
* Terraform -------- Infrastructure as Code
---
