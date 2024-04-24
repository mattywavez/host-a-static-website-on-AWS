![Alt text](/Host_a_Static_Website_on_AWS.png)

**Project: Hosting a Static Website on AWS**

This repository contains scripts and configurations to deploy a static HTML web application on AWS infrastructure. Below is an overview of the project setup and deployment process.

### Project Overview:
The project aims to host a static HTML web application on AWS, ensuring reliability, security, scalability, and fault tolerance. Key components and configurations include:

1. **Virtual Private Cloud (VPC)**:
   - Configured a VPC with public and private subnets across two availability zones for enhanced reliability.
   - Utilized Public Subnets for components like the NAT Gateway and Application Load Balancer.

2. **Internet Gateway (IGW)**:
   - Deployed an Internet Gateway to facilitate connectivity between VPC instances and the wider Internet.

3. **Security Groups**:
   - Established Security Groups as a network firewall mechanism to control traffic to EC2 instances.

4. **Availability Zones**:
   - Leveraged two Availability Zones to enhance system reliability and fault tolerance.

5. **EC2 Instances**:
   - Hosted the website on EC2 instances, positioning them within private subnets for enhanced security.
   - Implemented EC2 Instance Connect Endpoint for secure connections to assets within public and private subnets.

6. **NAT Gateway**:
   - Enabled instances in private subnets to access the Internet via the NAT Gateway.

7. **Application Load Balancer (ALB)**:
   - Employed an Application Load Balancer and a target group for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.

8. **Auto Scaling Group (ASG)**:
   - Utilized an Auto Scaling Group to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.

9. **GitHub Integration**:
   - Stored web files on GitHub for version control and collaboration.

10. **Certificate Manager**:
    - Secured application communications using AWS Certificate Manager.

11. **Simple Notification Service (SNS)**:
    - Configured SNS to alert about activities within the Auto Scaling Group.

12. **Route 53**:
    - Registered the domain name and set up a DNS record using Route 53.

### Deployment Script:
The deployment script provided automates the setup process for hosting the static website on an EC2 instance. Here's a summary of the script:

```bash
#!/bin/bash
# Switch to the root user to gain full administrative privileges
sudo su
# Update all installed packages to their latest versions
yum update -y
# Install Apache HTTP Server
yum install -y httpd
# Change the current working directory to the Apache web root
cd /var/www/html
# Install Git
yum install git -y
# Clone the project GitHub repository to the current directory
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/
# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws
# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd
# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

### Usage:
1. Ensure you have appropriate IAM permissions to deploy resources on AWS.
2. Execute the provided deployment script on an EC2 instance to set up and deploy the static website.
3. Access the website using the public IP or domain name associated with the EC2 instance.

For more detailed instructions and configurations, refer to the documentation and diagrams provided in the repository.

### Repository Structure:
- **diagrams/**: Contains diagrams illustrating the AWS infrastructure setup.
- **scripts/**: Includes deployment scripts and configurations.
- **README.md**: Detailed instructions and information about the project setup and deployment.

For any issues or questions, feel free to open an issue or contact the project owner.

---
