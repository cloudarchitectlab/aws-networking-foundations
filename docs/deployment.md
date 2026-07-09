# Deployment

## Purpose

This document describes the deployment process for **CAL-001 – AWS Networking Foundations**.

The objective is to provide a repeatable deployment procedure that provisions the networking infrastructure entirely through Infrastructure as Code using Terraform.

---

## Deployment Prerequisites

Before deploying this project, ensure the following requirements are met:

- AWS account with appropriate permissions
- AWS CLI installed and authenticated
- Terraform installed
- Git installed
- Visual Studio Code (recommended)

Verify the environment:

```bash
aws --version
terraform --version
git --version
```

---

## Deployment Workflow

The deployment process follows the standard Infrastructure as Code lifecycle.

```
Edit Terraform
        │
        ▼
terraform fmt
        │
        ▼
terraform validate
        │
        ▼
terraform plan
        │
        ▼
terraform apply
        │
        ▼
Verify in AWS
```

---

## Initialize Terraform

```bash
cd terraform
terraform init
```

Terraform downloads the required provider plugins and prepares the working directory.

---

## Review the Execution Plan

```bash
terraform plan
```

Review all proposed infrastructure changes before deployment.

---

## Deploy Infrastructure

```bash
terraform apply
```

Terraform provisions the AWS networking resources defined within the project.

---

## Verify Deployment

After deployment, verify:

- VPC created
- Public subnet created
- Internet Gateway attached
- Route table configured
- Security Group created
- Network ACL configured

Verification should be performed using both Terraform outputs and the AWS Management Console.

---

## Destroy Infrastructure

Because Cloud Architect Lab uses disposable lab environments, infrastructure should be removed when no longer required.

```bash
terraform destroy
```

Destroying unused resources helps minimize AWS costs and ensures future deployments begin from a known state.

---

## Future Automation

The deployment workflow is expected to become increasingly automated through CAL CLI.

Future capabilities may include:

- Environment validation
- Terraform formatting
- Terraform validation
- Diagram rendering
- Documentation validation
- Repository validation
- Automated publishing