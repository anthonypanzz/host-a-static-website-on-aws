# Host a Static Website on AWS

![Alt text](/Host_a_Static_Website_on_AWS.png)

---

## Project Overview
This project involves hosting a static HTML web application on AWS, leveraging a variety of AWS resources to ensure scalability, security, and reliability. The architecture is designed to provide high availability, fault tolerance, and secure connectivity using AWS best practices.

## Architecture & Resources Used
1. **Virtual Private Cloud (VPC):** Configured with both public and private subnets spanning two different availability zones.
![Screenshot 2025-02-02 060123](https://github.com/user-attachments/assets/c12ba916-b0b0-4945-8cbc-d3c54a3a8013)
---
2. **Internet Gateway:** Deployed to facilitate connectivity between VPC instances and the Internet.
![Screenshot 2025-02-02 060237](https://github.com/user-attachments/assets/bce9f1e8-df53-4904-93f0-66e3baccc5df)
---
3. **Security Groups:** Implemented as a firewall mechanism to control inbound and outbound traffic.
![Screenshot 2025-02-02 060619](https://github.com/user-attachments/assets/303bf695-4b4e-4098-a85d-b45cc25bcd91)
---
4. **Multi-AZ Deployment:** Leveraged two Availability Zones to enhance system reliability and fault tolerance.
![Screenshot 2025-02-02 064501](https://github.com/user-attachments/assets/c6959cc9-f29e-41d4-b0a7-513866998bca)
---
5. **Public Subnets:** Used for hosting infrastructure components like the NAT Gateway and Application Load Balancer.
![Screenshot 2025-02-02 060407](https://github.com/user-attachments/assets/c15e6ed7-0944-4ded-bfdb-e40030fea872)
---
6. **EC2 Instance Connect Endpoint:** Ensured secure connections to assets within both public and private subnets.
![Screenshot 2025-02-02 060732](https://github.com/user-attachments/assets/45e27b14-4e10-4c32-a3d4-f2bd0dcae744)
---
7. **Private Subnets:** Web servers (EC2 instances) were positioned within private subnets for enhanced security.
![Screenshot 2025-02-02 060407](https://github.com/user-attachments/assets/e269bd1e-9a63-4441-bf1c-b7cd152f3b95)
---
8. **NAT Gateway:** Enabled instances in private subnets to access the Internet while maintaining security.
![Screenshot 2025-02-02 060506](https://github.com/user-attachments/assets/4aa1fa9b-1612-4404-8b61-bdfbca727cc4)
---
9. **EC2 Instances:** Hosted the website on Amazon EC2 instances.
![Screenshot 2025-02-02 064501](https://github.com/user-attachments/assets/bef0c224-6ee2-49ec-bb42-350d8519c5dd)
---
10. **Application Load Balancer (ALB):** Used to evenly distribute web traffic across an Auto Scaling Group of EC2 instances.
![Screenshot 2025-02-02 060918](https://github.com/user-attachments/assets/4916ab6e-eaa1-4505-8e80-5a09ed8637b3)
![Screenshot 2025-02-02 062320](https://github.com/user-attachments/assets/80abd148-fb42-4c5c-a734-6a87c5cbc18a)
---
11. **Auto Scaling Group (ASG):** Automatically managed EC2 instances for high availability, scalability, and fault tolerance.
![Screenshot 2025-02-02 063523](https://github.com/user-attachments/assets/d167122a-6ade-4952-8a1b-ada5552cf477)
![Screenshot 2025-02-02 064251](https://github.com/user-attachments/assets/8a1e9821-fc14-4b6e-8f1f-4e7917d71ca4)
![Screenshot 2025-02-02 064501](https://github.com/user-attachments/assets/5609c4eb-0bf5-4310-85da-46a6717e9064)
![Screenshot 2025-02-02 064534](https://github.com/user-attachments/assets/9c4a881d-1782-4461-b7b3-94d65e204d24)
---
12. **GitHub Repository:** Stored web files for version control and collaboration.
---
13. **AWS Certificate Manager:** Secured application communications with SSL/TLS certificates.
![Screenshot 2025-02-02 062117](https://github.com/user-attachments/assets/e01a3d1d-eab9-4aa1-afda-6656cd396d98)
![Screenshot 2025-02-02 062552](https://github.com/user-attachments/assets/9f5ff19c-dd3e-42d2-a287-e65c0654feb8)
---
14. **Simple Notification Service (SNS):** Configured for alerts regarding Auto Scaling Group activities.
---
15. **Route 53:** Registered the domain name and configured DNS records.
![Screenshot 2025-02-02 061127](https://github.com/user-attachments/assets/b9dc7851-96fa-4406-a6bf-b7710105e44f)
![Screenshot 2025-02-02 062700](https://github.com/user-attachments/assets/6af06082-5e01-4850-ab50-48545679a6f7)
![Screenshot 2025-02-02 065015](https://github.com/user-attachments/assets/3d051b7c-f671-49de-b381-e7799ce7dd40)
![Screenshot 2025-02-02 065030](https://github.com/user-attachments/assets/70e67eb7-3379-4d23-827d-caadca21cb2b)
---
## Deployment Script
The following script automates the installation and setup of the web application on an EC2 instance:

```bash
#!/bin/bash
# Switch to root user
sudo su

# Update all installed packages
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change directory to Apache web root
cd /var/www/html

# Install Git
yum install git -y

# Clone the project repository
git clone https://github.com/anthonypanzz/host-a-static-website-on-aws.git

# Copy all files from the cloned repository to the web root
cp -R host-a-static-website-on-aws/. /var/www/html/

# Remove the cloned repository directory
rm -rf host-a-static-website-on-aws

# Enable Apache to start on boot
systemctl enable httpd

# Start the Apache HTTP Server
systemctl start httpd
```

## GitHub Repository
The reference architecture diagram and deployment scripts have been uploaded to the GitHub repository. You can access them at:
[GitHub Repository](https://github.com/anthonypanzz/host-a-static-website-on-aws)

## Conclusion
This project successfully demonstrates hosting a static website on AWS using EC2 instances, an Auto Scaling Group, and an Application Load Balancer. The setup ensures high availability, security, and automated scaling for a robust web hosting solution.


