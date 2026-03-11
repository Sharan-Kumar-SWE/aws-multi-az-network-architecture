# AWS VPC Auto Scaling Architecture Project

This project demonstrates how to deploy a scalable web application in AWS using a secure VPC architecture with private subnets and Auto Scaling.

The infrastructure includes an Application Load Balancer, frontend and backend servers inside private subnets, and MongoDB as the database.

This project was built to understand real-world DevOps infrastructure design including networking, load balancing, auto scaling, and secure server access.

---

# Live Application

Frontend  
https://vpc-setup.codetocloud.fun

API  
https://vpc-setupapi.codetocloud.fun

---

# Architecture Diagram

![Architecture](docs/images/architecture-diagram.png)

---

# Architecture Overview

The infrastructure is deployed inside an AWS VPC with both public and private subnets.

Public Subnet components:

• Internet Gateway  
• Bastion Host for SSH access  
• Application Load Balancer  
• NAT Gateway  

Private Subnet components:

• Frontend Server (React application served with Nginx)  
• Backend API Servers (Node.js running behind Auto Scaling Group)  
• MongoDB Database Server  

All application servers are placed inside private subnets for security.

Traffic flow:

User → Application Load Balancer → Private Servers

---

# Domain Routing

The Application Load Balancer routes traffic based on the domain name.

Frontend Route

vpc-setup.codetocloud.fun → Frontend Target Group → Frontend Server

API Route

vpc-setupapi.codetocloud.fun → Backend Target Group → Backend Auto Scaling Instances

SSL certificates are managed using AWS Certificate Manager.

---

# Tech Stack

Frontend  
React  
Nginx  

Backend  
Node.js  
Express.js  

Database  
MongoDB  

Cloud Infrastructure  
AWS EC2  
AWS VPC  
Application Load Balancer  
Auto Scaling Group  
NAT Gateway  
Internet Gateway  
AWS ACM  

---

# Infrastructure Design

VPC CIDR

10.0.0.0/16

Subnets

Public Subnets
- Bastion Host
- ALB
- NAT Gateway

Private Subnets
- Frontend Server
- Backend Auto Scaling Servers
- MongoDB Server

Security Strategy

• Only Bastion Host allows SSH from internet  
• Backend servers are accessible only through ALB  
• MongoDB accessible only from backend servers  

---

# Auto Scaling Configuration

Backend servers are deployed using an Auto Scaling Group.

Configuration:

Minimum instances: 1  
Desired instances: 1  
Maximum instances: 3  

Scaling Policy:

Scale out when CPU > 60%  
Scale in when CPU < 30%

When the backend instance CPU increases, the Auto Scaling Group launches new instances automatically.

When load decreases, extra instances are terminated automatically.

---

# Deployment Steps (High Level)

1 Create VPC with public and private subnets  
2 Create Internet Gateway and attach to VPC  
3 Create NAT Gateway for private subnet internet access  
4 Launch Bastion host in public subnet  
5 Launch frontend and backend servers in private subnet  
6 Install Nginx and deploy React application on frontend server  
7 Deploy Node.js API on backend server  
8 Install MongoDB on database server  
9 Create Application Load Balancer  
10 Configure ALB routing rules for frontend and API domains  
11 Create Auto Scaling Group for backend servers  

---

# Accessing Private Servers

Private servers are accessed using a Bastion host.

SSH Flow:

Local Machine → Bastion Host → Private Server

This ensures private servers are never directly exposed to the internet.

---

# Key DevOps Concepts Demonstrated

VPC Network Architecture  
Public vs Private Subnets  
Application Load Balancing  
Domain-based Routing  
SSL using ACM  
Auto Scaling Groups  
Secure SSH using Bastion Host  

---

# Future Improvements

Infrastructure as Code using Terraform  
CI/CD pipeline using GitHub Actions  
Blue-Green deployment strategy  
Containerization using Docker  
Kubernetes deployment using EKS  

---

# Author

Sharan Kumar

DevOps Engineer
