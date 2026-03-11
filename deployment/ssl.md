# SSL Configuration

HTTPS is enabled using AWS Certificate Manager.

Two SSL certificates were created for the domains.

vpc-setup.codetocloud.fun

vpc-setupapi.codetocloud.fun

Certificates were validated using DNS validation.

The certificates are attached to the HTTPS listener of the Application Load Balancer.
