# AWS 2-Tier Architecture (Web + Database)

## 📌 Overview

This project demonstrates the implementation of a secure 2-tier architecture using AWS services. It includes a web server hosted in a public subnet and a database server hosted in a private subnet within a Virtual Private Cloud (VPC).

---

## 🏗️ Architecture Components

* Amazon VPC (192.168.0.0/16)
* Public Subnet (Web Layer)
* Private Subnet (Database Layer)
* Internet Gateway (IGW)
* NAT Gateway
* EC2 (Apache Web Server)
* EC2 (PostgreSQL Database)

---

![Architecture](Two tier-architecture.png)

---

## 🔄 Architecture Flow

1. User accesses the web server via Internet Gateway
2. Web server processes request
3. Web server communicates with database using private IP
4. Database accesses internet via NAT Gateway for updates

---

## 🔐 Security

* Database is not publicly accessible
* Security Groups restrict access:

  * Web EC2: HTTP (80), SSH (22)
  * DB EC2: PostgreSQL (5432) from Web EC2 only

---

## 🚀 Implementation Steps

1. Create VPC
2. Create Public and Private Subnets
3. Attach Internet Gateway
4. Configure Route Tables
5. Create NAT Gateway
6. Launch EC2 instances
7. Configure Security Groups
8. Install Apache and PostgreSQL

---

## ✅ Testing

* Access web server via browser
* SSH into Web EC2
* Connect Web → DB using private IP
* Verify NAT using `ping google.com`

---

## 📊 Architecture Diagram

(Add your diagram image here)

---

## 🎯 Key Learnings

* VPC networking and subnet isolation
* Route tables and internet routing
* NAT Gateway usage
* Secure communication between tiers

---

## 📌 Conclusion

This project demonstrates a secure and scalable 2-tier architecture in AWS, following best practices for network isolation and controlled access.
