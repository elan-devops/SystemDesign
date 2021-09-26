# SystemDesign: Basic HTTPS

## Security Group: Security at Intance level
* Instances: private subnet - No access to Internet
* Default security group - any traffic with n/w instances of the SG or by itself

## DNS:
* Internal DNS to route all the internal n/w to the internal LB to avoid latency
* External DNS to route any internet traffic to the external LB (outside world)

## Load balancer: (ALB)
* External LB - public subnet with route table connected to igw (0.0.0.0/0)
* Security group to allow 443/80 traffic (Ingress) from internet and
* Egress to Instances in Private subnet via Listeners at 80 (http)/ 443 (https)
* TLS - SSL certificate
* Health check at different / endpoints
* NAT - For private instances to connect to public subnet ELB (where each subnet in az of private subnets) 

## Containers:
* Docker container in Instances serving web traffic (sample python flask)

## NACL: Security at Subnet levels
* Default or we can specify just 80/ 443 and rest all denied

