## AWS Infrastructure Provisioning using Terraform & Jenkins CI/CD

### Overview

This project automates AWS infrastructure provisioning using Terraform and Jenkins CI/CD. It integrates GitHub with Jenkins to automatically trigger pipeline execution whenever code changes are pushed to the repository.

The pipeline follows Infrastructure as Code (IaC) best practices by validating Terraform configurations, generating execution plans, and requiring manual approval before applying infrastructure changes.

Infrastructure state is securely stored in an Amazon S3 backend, enabling centralized state management and supporting collaboration.

## Architecture

```mermaid
flowchart TD
    A[Developer] -->|Git Push| B[GitHub Repository]

    B -->|Webhook| C[Jenkins Server on EC2]

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


