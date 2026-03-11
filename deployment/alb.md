# Application Load Balancer

An Application Load Balancer is used to distribute traffic to application servers.

The load balancer is deployed in public subnets and accepts internet traffic.

---

## Listeners

HTTP : 80  
HTTPS : 443

HTTPS traffic is secured using SSL certificates managed by AWS Certificate Manager.

---

## Host-Based Routing

Two hostnames are configured.

Frontend:

vpc-setup.codetocloud.fun

Backend API:

vpc-setupapi.codetocloud.fun

Routing rules:

vpc-setup.codetocloud.fun → Frontend Target Group

vpc-setupapi.codetocloud.fun → Backend Target Group

---

## Health Checks

The load balancer performs health checks on backend instances to ensure traffic is only sent to healthy servers.
