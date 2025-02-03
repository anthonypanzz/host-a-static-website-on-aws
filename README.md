![Alt text](/Host_a_Static_Website_on_AWS.png)

# Host a Static Website on AWS

## Project Overview
This project involves hosting a static HTML web application on AWS, leveraging a variety of AWS resources to ensure scalability, security, and reliability. The architecture is designed to provide high availability, fault tolerance, and secure connectivity using AWS best practices.

## Architecture & Resources Used
1. **Virtual Private Cloud (VPC):** Configured with both public and private subnets spanning two different availability zones.
2. **Internet Gateway:** Deployed to facilitate connectivity between VPC instances and the Internet.
3. **Security Groups:** Implemented as a firewall mechanism to control inbound and outbound traffic.
4. **Multi-AZ Deployment:** Leveraged two Availability Zones to enhance system reliability and fault tolerance.
5. **Public Subnets:** Used for hosting infrastructure components like the NAT Gateway and Application Load Balancer.
6. **EC2 Instance Connect Endpoint:** Ensured secure connections to assets within both public and private subnets.
7. **Private Subnets:** Web servers (EC2 instances) were positioned within private subnets for enhanced security.
8. **NAT Gateway:** Enabled instances in private subnets to access the Internet while maintaining security.
9. **EC2 Instances:** Hosted the website on Amazon EC2 instances.
10. **Application Load Balancer (ALB):** Used to evenly distribute web traffic across an Auto Scaling Group of EC2 instances.
11. **Auto Scaling Group (ASG):** Automatically managed EC2 instances for high availability, scalability, and fault tolerance.
12. **GitHub Repository:** Stored web files for version control and collaboration.
13. **AWS Certificate Manager:** Secured application communications with SSL/TLS certificates.
14. **Simple Notification Service (SNS):** Configured for alerts regarding Auto Scaling Group activities.
15. **Route 53:** Registered the domain name and configured DNS records.

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


