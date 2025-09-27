# ☁️ Multi-Cloud Photo Album Website – AWS + OCI Deployment

The **Multi-Cloud Photo Album Website** is a secure and resilient cloud application deployed across **Amazon Web Services (AWS)** and **Oracle Cloud Infrastructure (OCI)**.  
It demonstrates a **hybrid multi-cloud architecture**, where **AWS hosts the web server** and **OCI hosts the database and object storage**, connected through a **private IPsec VPN tunnel**.  

---

## 📌 Features

- 🌐 **Web Application on AWS**: PHP/Apache web server deployed on Amazon EC2.  
- 🛡️ **Multi-Cloud Networking**: Secure Virtual Private Clouds (VPCs/VCNs) configured in AWS and OCI.  
- 🔒 **Private Database Access**: MySQL database on OCI, only accessible via **private IP through IPsec VPN**.  
- 📂 **OCI Object Storage**: Stores and serves photo files with public read-only access.  
- ⚙️ **VPN Connectivity**: Configured **IPsec tunnel** between AWS and OCI to enable secure communication.  
- 🛠️ **Security Controls**: Security Groups, Network Security Groups (NSGs), and ACLs enforce least-privilege access.  

---

## 🌟 Project Overview

The deployment was structured into three major parts:

### 🔹 Part 1: Oracle Cloud Infrastructure (OCI) Setup
- Created a **VCN (MyVCN)** with **public and private subnets**.  
- Configured **Security Lists** and **Network Security Groups (Web-tier NSG)** for HTTP/HTTPS traffic.  
- Launched a **MySQL 8.0 database** in the private subnet for secure data storage.  
- Created an **OCI Object Storage bucket** to host and serve photo files.  

### 🔹 Part 2: Amazon Web Services (AWS) Setup
- Created a **VPC (MyVPC)** with **public and private subnets**.  
- Deployed a **web server instance (Amazon Linux 2)** in the public subnet, configured with **Apache + PHP**.  
- Installed **phpMyAdmin** for managing the OCI MySQL database remotely.  
- Configured **Security Groups** for web-tier (HTTP/HTTPS + MySQL) and test instances.  
- Applied **Network ACLs** to further secure inbound/outbound traffic.  

### 🔹 Part 3: IPsec VPN Tunnel Configuration
- On OCI: Created **Dynamic Routing Gateway (DRG)**, **CPE**, and **IPSec connection**.  
- On AWS: Configured **Virtual Private Gateway (VPG)**, **Customer Gateway (CGW)**, and **VPN connection**.  
- Established routing rules to ensure AWS web server could connect to OCI MySQL over **private IP only**.  
- Verified connectivity by accessing MySQL from the AWS instance securely.  

---

## 🏗️ Architecture

<img width="929" height="562" alt="image" src="https://github.com/user-attachments/assets/4468f491-4839-4d2f-b4e6-9ff5b7c20ae1" />


---

## 🛠️ Tech Stack

- **Cloud Platforms**: Amazon Web Services (AWS), Oracle Cloud Infrastructure (OCI)  
- **Compute**: AWS EC2 (Web Server), OCI Compute (Testing)  
- **Database**: MySQL 8.0 on OCI + phpMyAdmin  
- **Storage**: OCI Object Storage (public read access)  
- **Networking**: VPC (AWS), VCN (OCI), Subnets, Routing Tables  
- **Security**: Security Groups, NSGs, NACLs, IAM policies  
- **Connectivity**: IPsec VPN Tunnel (AWS ↔ OCI)  
- **Languages & Tools**: PHP, Apache, SQL, MySQL, phpMyAdmin  

---

## 🔒 Security Best Practices

- Database hosted in a **private subnet** on OCI (not publicly accessible).  
- **IPsec VPN ensures encrypted cross-cloud communication**.  
- **Least-privilege rules** applied using Security Groups, NSGs, and ACLs.  
- Public access limited only to HTTP/HTTPS on the web server and photo storage bucket.  

---

## 🚀 Future Enhancements

- 🔐 Enable **multi-factor authentication (MFA)** for admin access.  
- 📈 Use **OCI Monitoring** and **AWS CloudWatch** for observability.  
- 🔒 Add **SSL/TLS certificates** for HTTPS across both clouds.  
- ⚡ Deploy an **Elastic Load Balancer (AWS)** and **OCI Load Balancer** for scalability.  
