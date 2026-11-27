## AWS Infrastructure Provisioning using Terraform & Jenkins CI/CD

#### Overview

This project automates AWS infrastructure provisioning using Terraform and Jenkins CI/CD. It integrates GitHub with Jenkins to automatically trigger pipeline execution whenever code changes are pushed to the repository.

The pipeline follows Infrastructure as Code (IaC) best practices by validating Terraform configurations, generating execution plans, and requiring manual approval before applying infrastructure changes.

Infrastructure state is securely stored in an Amazon S3 backend, enabling centralized state management and supporting collaboration.
