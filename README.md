Project Title: CloudLaunch Deployment — AWS Cloud Engineering Assignment

Description

This project showcases a step-by-step deployment of a simple cloud infrastructure using AWS services — S3, EC2, IAM, VPC, Nginx, and MongoDB. It was built as part of AltSchool Africa’s Cloud Engineering Diploma program.



Architecture Overview

Frontend (Static Website): Hosted on S3 bucket with public read policy.

Backend (Application Layer): Ubuntu EC2 instance running Nginx.

Database Layer: MongoDB service installed on same EC2 instance.

IAM Role: EC2 assumes CloudLaunchEC2Role for S3 read-only access.

Networking: Custom VPC with subnets, route table, and internet gateway.




Tools & Technologies

AWS Services: S3, EC2, IAM, VPC

Software: Ubuntu 24.04 (Noble), Nginx, MongoDB 7.0

Access Tools: AWS CLI, Termius SSH, Git, Visual Studio Code

Region: eu-west-1 (Ireland)




Commands Summary

# Create S3 Buckets
aws s3 mb s3://cloudlaunch-site-bucket-altschooluser1 --region eu-west-1
aws s3 mb s3://cloudlaunch-private-bucket-altschooluser1 --region eu-west-1
aws s3 mb s3://cloudlaunch-visible-only-bucket-altschooluser1 --region eu-west-1

# Upload HTML File
aws s3 cp index.html s3://cloudlaunch-site-bucket-altschooluser1/

# Check Buckets
aws s3 ls

# Install Nginx & MongoDB
sudo apt update -y && sudo apt install nginx -y
sudo apt install -y mongodb-org
sudo systemctl start mongod && sudo systemctl enable mongod

# Verify Role and CLI
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/
aws s3 ls

Outputs (Verification Screenshots)

✅ S3 buckets listed in AWS Console.

✅ HTML file accessible via public URL.

✅ EC2 instance running in VPC with IAM role.

✅ Nginx welcome page live.

✅ MongoDB running and verified.

✅ AWS CLI lists S3 buckets using instance credentials.



Author

Light Ibeh
Cloud Engineering Student at AltSchool Africa
