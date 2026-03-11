# VPC Configuration

A custom VPC was created to host the infrastructure.

VPC CIDR block:

10.0.0.0/16

---

## Subnets

Two types of subnets were created.

Public Subnets:

Used for internet-facing resources.

- Load Balancer
- Bastion Host

Private Subnets:

Used for application servers.

- Frontend EC2 instance
- Backend EC2 instances
- MongoDB server

---

## Internet Gateway

An Internet Gateway is attached to the VPC to allow internet access for public subnet resources.

---

## NAT Gateway

Private subnet instances use NAT Gateway for outbound internet access such as installing packages or updates.
