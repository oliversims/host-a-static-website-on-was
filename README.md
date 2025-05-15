![Alt text](/Host_a_Static_Website_on_AWS.png)
# 🌐 Host a Static Website on AWS

This project demonstrates how to host a **static HTML website** on AWS using a complete DevOps infrastructure, deployed across multiple availability zones for high availability, scalability, and security.

## 🚀 Project Architecture

This project includes the following AWS resources and features:

1. ✅ **VPC** with both **public and private subnets** across two Availability Zones for fault tolerance.
2. 🌐 **Internet Gateway** to enable external access to public resources.
3. 🔐 **Security Groups** used as firewalls to control inbound and outbound traffic.
4. 🏗️ **Two Availability Zones** to increase system reliability and fault tolerance.
5. 🛠️ **Public Subnets** used for NAT Gateway and Application Load Balancer (ALB).
6. 🔌 **EC2 Instance Connect Endpoint** for secure SSH access to private instances.
7. 🛡️ **EC2 Web Servers** positioned in private subnets for enhanced security.
8. 🌍 **NAT Gateway** to allow private instances to access the internet.
9. 💻 **Static Website** hosted on EC2 instances (Apache).
10. ⚖️ **Application Load Balancer** for distributing traffic to EC2 instances in an Auto Scaling Group.
11. 📈 **Auto Scaling Group** for elasticity and high availability of EC2 instances.
12. 🗂️ **GitHub** used for storing website files and deployment script (version control).
13. 🔐 **AWS Certificate Manager (ACM)** for securing application traffic via HTTPS.
14. 📩 **Amazon SNS** for alerting on Auto Scaling Group activities.
15. 🌐 **Route 53** for domain registration and DNS record management.

---

## 🧰 Deployment Script (User Data)

The EC2 user data script used to deploy the web server:

```bash
#!/bin/bash
sudo su
yum update -y
yum install -y httpd
cd /var/www/html
yum install git -y
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
cp -R host-a-static-website-on-aws/. /var/www/html/
rm -rf host-a-static-website-on-aws
systemctl enable httpd
systemctl start httpd
