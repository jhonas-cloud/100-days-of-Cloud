# 100 Days of Cloud - Day 3

## Creating a Subnet

# Overview
An AWS subnet is a range of IP addresses (defined by a CIDR block) inside a VPC that lets you organize and control your network resources.

### Key characteristics of a subnet <br>

# 1️⃣ Has a CIDR block

VPC:    172.31.0.0/16 <br>
Subnet: 172.31.0.0/24

This CIDR block defines how many IPs the subnet has.

# 2️⃣ Lives in ONE Availability Zone <br>

- A subnet cannot span multiple AZs <br>
- This is why you usually create one subnet per AZ

# 3️⃣ Can be public or private

Public subnet
- Route table has a route to an Internet Gateway
- Used for: ALB, Bastion hosts, public EC2 <br>

Private subnet 
- No direct route to the internet
- Used for: App servers, databases

# 4️⃣ AWS reserves 5 IP addresses

In every subnet, AWS automatically reserves:
- Network address <br>
- VPC router <br>
- DNS <br>
- Future use <br>
- Broadcast <br>
So a /24 subnet: <br>
- 256 total IPs
- 251 usable

# 5️⃣ Controlled by routing & security

Traffic is governed by: <br>
- Route tables (where traffic goes) <br>
- Security Groups (instance-level firewall) <br>
- NACLs (subnet-level firewall) <br>

# Why subnets matter <br>

Subnets help you:
- Separate public vs private resources
- Control traffic flow
- Improve security
- Design for high availability
- Scale cleanly

**Day 3 Complete!**