# AWS Two-Tier Architecture Using Load Balancers

## Project Overview
This project demonstrates the implementation of a **Two-Tier Architecture in AWS**, where a **Web Server** communicates with an **Application Server** using **public and private Network Load Balancers**. The architecture is designed following best practices for security, scalability, and availability.


---

## 🎯 Objective
To establish secure and efficient communication between a **Web Server** and an **Application Server** using **AWS Load Balancers**, while isolating backend resources in private subnets.

---

## Architecture Description
- Web Server deployed in a **Public Subnet**
- App Server deployed in a **Private Subnet**
- Public Network Load Balancer for external access
- Private Network Load Balancer for internal communication
- Secure access using Security Groups
- VPC with proper routing via Internet Gateway

---

## AWS Services Used
- Amazon EC2  
- Amazon VPC  
- Public & Private Subnets  
- Internet Gateway  
- Route Tables  
- Security Groups  
- Network Load Balancers (Public & Private)  
- Target Groups  

---

## Architecture Flow
1. User accesses the application through the **Public Load Balancer**
2. Traffic is routed to the **Web Server**
3. Web Server communicates with the **App Server** via **Private Load Balancer**
4. App Server responds securely within the private network

---

## Implementation Steps

### 1️⃣ Network Setup
- Create a VPC (CIDR: `10.0.0.0/16`)
- Create Public and Private Subnets
- Create and attach Internet Gateway
- Configure Route Tables for public access

### 2️⃣ Security Configuration
- Create Security Groups
- Allow required inbound ports (HTTP, SSH, 8080)
- Restrict private access to internal traffic only

### 3️⃣ EC2 Instances
- Launch Web Server EC2 in Public Subnet
- Launch App Server EC2 in Private Subnet
- Connect using MobaXterm

### 4️⃣ Web Server Setup
```bash
sudo su
apt update
apt install nginx -y

---

## App Server Setup
sudo su
apt update
apt install default-jdk -y
wget https://dlcdn.apache.org/tomcat/tomcat-11/v11.0.18/bin/apache-tomcat-11.0.18.tar.gz
tar -xvf apache-tomcat-11.0.18.tar.gz
mv apache-tomcat-11.0.18 tomcat
cd tomcat/bin
./startup.sh

