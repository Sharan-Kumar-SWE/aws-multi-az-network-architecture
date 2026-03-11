# Architecture Explanation

This project uses a secure AWS architecture to host a scalable web application.

The infrastructure is built inside a custom VPC.

## Public Subnet

The public subnet contains components that must be accessible from the internet.

Resources:

- Application Load Balancer
- Bastion Host for SSH access

The load balancer receives all incoming traffic and routes requests to private application servers.

---

## Private Subnet

Application servers are deployed in private subnets to improve security.

Resources:

- Frontend EC2 instance
- Backend EC2 instances (Auto Scaling Group)
- MongoDB database server

These servers are not directly accessible from the internet.

Access is only allowed through the load balancer or bastion host.

---

## Traffic Flow

User

↓

DNS resolution

↓

Application Load Balancer

↓

Host based routing

↓

Frontend or Backend servers

↓

Database
