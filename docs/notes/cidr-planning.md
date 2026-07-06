# CIDR Planning Notes

## Why use a /16 VPC?

For this lab, I am using a `/16` CIDR block for the VPC because it provides a large private address space while still allowing me to divide the network into smaller, organized subnets.

Example:

```text
VPC CIDR: 10.0.0.0/16