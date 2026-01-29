# 100 Days of Cloud - Day 2

## Create Security Group

### Overview
A security group is basically a virtual firewall. It controls who’s allowed in and out of a resource (like a server or database) on a network.

## In simple terms
A security group:
- Defines rules
- Rules say what traffic is allowed
- Everything not explicitly allowed is blocked
## What kind of rules?
Rules are usually based on:
- Protocol (TCP, UDP, ICMP, etc.)
- Port number (like 22 for SSH, 80 for HTTP, 443 for HTTPS)
- Source or destination (IP address, range, or another security group)
## Example:
- “Allow HTTP (port 80) from anywhere”
- “Allow SSH (port 22) only from my IP”

## Key characteristics
- Stateful: if inbound traffic is allowed, the response traffic is automatically allowed back
- Inbound rules: who can reach your resource
- Outbound rules: where your resource can send traffic
- Applied to instances/resources, not the whole network

## Common use cases
- Protecting servers from public internet access
- Allowing database access only from app servers
- Limiting admin access to specific IPs