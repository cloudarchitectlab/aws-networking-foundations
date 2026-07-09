# Design Decisions

## Purpose

This document records the significant architectural decisions made during the design and implementation of **CAL-001 – AWS Networking Foundations**.

Rather than documenting every implementation detail, this document explains the rationale behind key design choices and the tradeoffs that influenced them. More formal or long-lived decisions may also be captured as individual Architecture Decision Records (ADRs) within the `docs/adr/` directory.

---

## Decision 1 — Create a Custom VPC

### Decision

Deploy a dedicated Virtual Private Cloud rather than using the default VPC provided by AWS.

### Rationale

Although AWS automatically creates a default VPC in each Region, production environments commonly use custom VPCs to provide complete control over IP addressing, subnet design, routing, and security boundaries.

Building a custom VPC also mirrors enterprise cloud practices and provides a clean foundation for future expansion.

---

## Decision 2 — Build with Infrastructure as Code

### Decision

Provision all infrastructure using Terraform.

### Rationale

Infrastructure as Code provides repeatability, version control, peer review, and consistent deployments. It also minimizes configuration drift by ensuring infrastructure is recreated from source rather than manually configured.

---

## Decision 3 — Document Architecture as Code

### Decision

Maintain architecture diagrams as Mermaid source files and generate SVG diagrams for documentation.

### Rationale

Treating architecture diagrams as source artifacts ensures that architectural documentation evolves alongside the infrastructure code. Version-controlled diagrams also support collaboration, change tracking, and automated publishing workflows.

---

## Decision 4 — Keep the Initial Architecture Intentionally Simple

### Decision

Begin with a minimal networking implementation before introducing advanced networking components.

### Rationale

Establishing a clear and well-understood foundation simplifies troubleshooting and provides a stable baseline for future enhancements such as private subnets, NAT Gateways, multi-AZ deployments, and VPC peering.

---

## Decision 5 — Separate Repository Documentation by Responsibility

### Decision

Organize project documentation into focused documents rather than a single large design document.

### Rationale

Separating architecture, deployment, validation, lessons learned, and design decisions makes the documentation easier to maintain and aligns with the future publishing workflow planned for Cloud Architect Lab and CAL CLI.

---

## Future Decisions

As the project evolves, additional architectural decisions may include:

- CIDR allocation strategy
- Multi-AZ design
- NAT Gateway placement
- Security Group strategy
- Network ACL usage
- Route table organization
- High availability considerations
- Cost optimization decisions

Significant long-term decisions should also be documented as individual Architecture Decision Records (ADRs) when appropriate.