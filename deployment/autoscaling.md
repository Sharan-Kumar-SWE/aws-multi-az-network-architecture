# Auto Scaling Configuration

Backend servers are managed using an Auto Scaling Group.

This allows the application to automatically handle traffic spikes.

---

## Launch Template

A launch template was created using a backend AMI.

The template defines:

- AMI ID
- Instance type
- Security group
- Network configuration

---

## Auto Scaling Settings

Minimum instances: 1  
Desired instances: 1  
Maximum instances: 4  

---

## Scaling Policy

Target tracking scaling policy based on CPU utilization.

Target CPU utilization:

60%

If CPU usage exceeds the target, new instances are automatically launched.

When traffic decreases, extra instances are terminated automatically.
