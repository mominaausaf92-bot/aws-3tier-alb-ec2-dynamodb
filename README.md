# AWS 3-Tier Web Architecture Project (ALB + EC2 + DynamoDB)

## Project Overview

This project demonstrates a basic highly available web architecture built on Amazon Web Services (AWS).
The goal was to practice real-world cloud infrastructure concepts including networking, load balancing, compute services, and managed databases.

The architecture distributes traffic across multiple EC2 web servers using an Application Load Balancer and stores application data in DynamoDB.

---

## Architecture

User
↓
Application Load Balancer
↓
Target Group
↓
EC2 Web Servers (Apache)
↓
DynamoDB Database

---

## AWS Services Used

* Amazon VPC
* Public Subnets
* Private Subnets
* Internet Gateway
* Route Tables
* Security Groups
* EC2 (Amazon Linux 2023)
* Apache Web Server
* Application Load Balancer (ALB)
* Target Groups & Health Checks
* DynamoDB
* IAM Role for EC2

---

## Project Steps

### 1. VPC and Networking

* Created a custom VPC
* Configured public and private subnets across multiple Availability Zones
* Attached an Internet Gateway to allow internet access
* Configured route tables for proper network routing

### 2. EC2 Web Servers

* Launched two EC2 instances using Amazon Linux
* Installed Apache web server
* Created a simple webpage for testing
* Verified server responses locally using curl

### 3. Application Load Balancer

* Created an Application Load Balancer
* Configured a Target Group
* Registered EC2 instances as targets
* Configured health checks to monitor server status

### 4. Security Configuration

* Configured Security Groups to allow:

  * HTTP traffic from the Load Balancer
  * SSH access from a specific IP address
* Ensured proper communication between services

### 5. DynamoDB Database

* Created a DynamoDB table with a partition key
* Inserted and retrieved test data using AWS CLI
* Verified database connectivity

---

## Example Commands Used

Install Apache on EC2

```
sudo dnf install -y httpd
sudo systemctl enable httpd
sudo systemctl start httpd
```

Create test webpage

```
echo "<h1>Server Working</h1>" | sudo tee /var/www/html/index.html
```

Add item to DynamoDB

```
aws dynamodb put-item \
--table-name webapp-db \
--item '{"string":{"S":"1"},"message":{"S":"Hello from EC2"}}' \
--region eu-west-1
```

---

## Project Screenshots

Screenshots of the infrastructure setup, EC2 servers, ALB configuration, and DynamoDB operations are included in the **screenshots/** folder.

---

## Key Learning Outcomes

* Hands-on experience with AWS networking
* Deploying scalable web infrastructure
* Configuring load balancing and health checks
* Integrating EC2 with DynamoDB
* Understanding secure cloud architecture

---

## Future Improvements

* Add Auto Scaling Group for dynamic scaling
* Move EC2 instances into private subnets
* Implement CI/CD pipeline for automated deployments
* Add monitoring with Amazon CloudWatch

---

## Author

Cloud project built as part of hands-on AWS learning and cloud engineering practice.
