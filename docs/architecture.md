# Architecture

## Purpose

This document describes the architecture of **CAL-001 – AWS Networking Foundations**, including the network topology, design principles, and architectural decisions that establish the baseline for future Cloud Architect Lab case studies.

The objective of this project is to build a secure, repeatable AWS networking foundation using Infrastructure as Code (Terraform) while following cloud architecture best practices.

---

## Solution Overview

The architecture consists of a custom Amazon Virtual Private Cloud (VPC) deployed within a single AWS Region.

The initial implementation establishes the foundational networking components required for future workloads:

- Custom Virtual Private Cloud (VPC)
- Public Subnet
- Internet Gateway
- Route Table
- Network ACL
- Security Group

This networking layer serves as the base upon which future case studies will build additional capabilities, including private subnets, NAT Gateways, EC2 instances, VPC Peering, and multi-AZ architectures.

---

## Design Principles

### Infrastructure as Code

All infrastructure is defined using Terraform and stored in version control. Infrastructure should never rely on manual configuration through the AWS Management Console.

### Architecture as Code

Architecture diagrams are maintained as Mermaid source files and rendered into SVG assets. The diagram source is version-controlled alongside the infrastructure code, ensuring the architecture documentation evolves with the implementation.

### Repeatability

The environment can be recreated consistently from source using Terraform, reducing configuration drift and enabling reproducible deployments.

### Simplicity

The initial architecture intentionally focuses on foundational AWS networking concepts before introducing additional complexity. Each future enhancement builds upon this baseline rather than replacing it.

---

## Architecture Components

### Virtual Private Cloud (VPC)

The VPC provides logical isolation for cloud resources and defines the project's private network boundary.

### Public Subnet

The public subnet hosts resources that require direct internet connectivity through the Internet Gateway.

### Internet Gateway

The Internet Gateway enables communication between resources in the public subnet and the public Internet.

### Route Table

The route table controls network routing within the VPC and directs internet-bound traffic through the Internet Gateway.

### Network ACL

The Network Access Control List (NACL) provides stateless subnet-level traffic filtering.

### Security Group

Security Groups provide stateful instance-level traffic filtering and act as the primary security boundary for compute resources deployed within the VPC.

---

## Network Topology

The current architecture consists of a single VPC containing one public subnet with controlled internet access through an Internet Gateway.

The complete architecture is documented in the following assets:

- Source: `diagrams/source/aws-networking-foundations.mmd`
- Rendered Diagram: `diagrams/exported/aws-networking-foundations.svg`

---

## Architectural Constraints

This project intentionally omits several production-oriented components while focusing on foundational networking concepts.

Current exclusions include:

- Private subnets
- NAT Gateway
- Multiple Availability Zones
- Transit Gateway
- VPN connectivity
- Direct Connect
- Hybrid networking

These capabilities will be introduced in subsequent Cloud Architect Lab case studies.

---

## Relationship to Future Projects

This project establishes the networking foundation for future Cloud Architect Lab implementations.

Planned projects will expand this architecture to include:

- CAL-002 – AWS VPC Peering
- Multi-AZ networking
- EC2 application workloads
- Secure private networking
- Enterprise routing strategies
- Hybrid and multi-cloud connectivity

Each future case study will build upon the architectural patterns established in CAL-001 rather than introducing unrelated designs.