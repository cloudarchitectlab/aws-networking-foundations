# Network Design

## Business Scenario

This case study demonstrates the design of a scalable AWS network foundation for a regulated enterprise environment.

The objective is to provide secure networking that supports public-facing services, private application workloads, future expansion, and Infrastructure as Code using Terraform.

## Design Principles

- Security by design
- Least privilege
- High availability
- Scalability
- Repeatable deployment using Infrastructure as Code
- Clear separation of network tiers

## Proposed Network

VPC
- 10.0.0.0/16

Availability Zone A
- Public Subnet
- Private Application Subnet

Availability Zone B
- Public Subnet
- Private Application Subnet

Shared Components
- Internet Gateway
- NAT Gateway (lab design)
- Route Tables
- Security Groups
- Network ACLs

## Future Expansion

The network is intentionally designed to support future additions, including:

- Database subnets
- Management subnets
- Inspection subnets
- VPC Peering
- Transit Gateway
- Hybrid connectivity
- IPv6

## NAT Gateway Design Decision

For this learning environment, the design uses a single NAT Gateway instead of one NAT Gateway per Availability Zone.

A NAT Gateway allows private subnet resources to initiate outbound internet connections for tasks such as operating system updates, software package downloads, and patching, while preventing direct inbound internet access.

In a production environment, one NAT Gateway per Availability Zone is generally preferred. That design improves availability, avoids cross-AZ dependencies, and reduces the risk that private resources in one Availability Zone lose outbound internet access because of a failure in another Availability Zone.

For this case study, a single NAT Gateway is selected to reduce cost and keep the lab focused on foundational AWS networking concepts. NAT Gateways incur hourly charges, so minimizing the number of NAT Gateways is appropriate for a temporary learning environment.

This design intentionally favors cost control and simplicity while documenting the production-grade alternative.

## Lab vs. Production NAT Pattern

| Environment | NAT Gateway Pattern | Reason |
|------|------------------|--------------|
| Lab / learning | One NAT Gateway | Lower cost and simpler design |
| Production | One NAT Gateway per Availability Zone | Higher availability and reduced cross-AZ dependency |

