# AWS 3-Tier Architecture using Terraform

This project provisions a **Basic 3-Tier Architecture** in AWS using Terraform.

---

# 🏗 Architecture Overview

## Architecture Diagram

![Architecture Diagram](screenshots/3tier_project_flow.png)

### Traffic Flow

Internet → Proxy Server → Application Server → RDS Database

---

# 📦 Infrastructure Components

## 1️⃣ VPC

- CIDR: `10.0.0.0/16`
- DNS Hostnames Enabled

📸 Screenshot:

![VPC](images/vpc.png)

---

## 2️⃣ Subnets

| Subnet | CIDR | Purpose |
|--------|------|----------|
| Public | 10.0.1.0/24 | Proxy EC2 |
| Private App | 10.0.2.0/24 | App EC2 |
| Private DB | 10.0.3.0/24 | RDS |

📸 Screenshot:

![Subnets](images/subnets.png)

---

## 3️⃣ Internet Gateway

Allows public internet access for proxy server.

📸 Screenshot:

![Internet Gateway](images/igw.png)

---

## 4️⃣ NAT Gateway

Allows private subnet instances to access the internet securely.

📸 Screenshot:

![NAT Gateway](images/NAT.png)

---

## 5️⃣ EC2 Instances (t3.micro)

- Proxy Server (Public Subnet)
- Application Server (Private Subnet)

📸 Screenshot:

![EC2 Instances](images/ec2.png)

---

## 6️⃣ RDS Database (MySQL)

- Instance Type: `db.t3.micro`
- Not Publicly Accessible
- Accessible only from App server

📸 Screenshot:

![RDS](images/RDS.png)

---

# 🔐 Security Architecture

- Proxy allows HTTP (80) and SSH (22) from Internet
- App allows traffic only from Proxy Security Group
- RDS allows MySQL (3306) only from App Security Group
- RDS is not publicly accessible

---
