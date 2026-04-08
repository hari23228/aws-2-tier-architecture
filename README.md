# AWS 2-Tier Architecture (Web + Database)

## 📌 Overview

This project demonstrates the design and implementation of a secure 2-tier architecture using AWS services. The architecture is built within a Virtual Private Cloud (VPC), consisting of a public subnet for the web layer and a private subnet for the database layer, ensuring proper network isolation and security.

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

## 📊 Architecture Diagram

![Architecture](Two%20tier%20-%20architecture.png)

---

## 🔄 Architecture Flow

1. User sends request from the internet
2. Request reaches Internet Gateway (IGW)
3. IGW routes traffic to Web Server (EC2 in Public Subnet)
4. Web Server processes request and communicates with Database (Private EC2) using private IP
5. Database sends outbound traffic via NAT Gateway for updates
6. Response is sent back to the user through IGW

---

## 🔐 Security

* Database is not publicly accessible (Private Subnet)
* Security Groups enforce restricted access:

  * Web EC2:

    * HTTP (80) → 0.0.0.0/0
    * SSH (22) → My IP
  * DB EC2:

    * PostgreSQL (5432) → Web EC2 only
    * SSH (22) → Web EC2 only

---

## 🚀 Implementation Steps

1. Create VPC with CIDR block
2. Create Public and Private Subnets
3. Attach Internet Gateway to VPC
4. Configure Public Route Table (IGW)
5. Create NAT Gateway in Public Subnet
6. Configure Private Route Table (NAT Gateway)
7. Create Security Groups
8. Launch EC2 instances (Web & Database)
9. Install Apache (Web Server)
10. Install PostgreSQL (Database Server)

---

## ✅ Testing

* Access web server via browser using public IP
* SSH into Web EC2 instance
* Connect to DB EC2 using private IP from Web EC2
* Verify internet access from private EC2 using:

  ```bash
  ping google.com
  ```

---

## 🎯 Key Learnings

* VPC design and subnet isolation
* Route tables and traffic flow
* Internet Gateway vs NAT Gateway
* Secure communication using Security Groups
* Public vs Private subnet behavior

---

## 📌 Conclusion

This project demonstrates a secure and scalable 2-tier AWS architecture by separating web and database layers into different subnets. It follows best practices for network security, controlled access, and efficient resource communication within a cloud environment.


## 📄 Documentation

For a detailed explanation of the architecture, implementation steps, please refer to the attached document:

[Two Tier Application using Private Network](./Two%20tier%20Application%20using%20private%20network.docx)
