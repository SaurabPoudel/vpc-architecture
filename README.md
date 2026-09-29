# DevOps Project 02

## Overview
This project is a simple DevOps-focused web deployment and cloud infrastructure exercise. It combines a static website with AWS automation to demonstrate how a company landing page can be hosted on an EC2 instance, retrieved from S3, and monitored using CloudWatch and VPC Flow Logs.

The repository includes:
- a static HTML/CSS/JavaScript business website under the html-web-app folder
- an EC2 bootstrap script that installs Apache, loads content from S3, and configures monitoring
- AWS IAM and logging configuration examples for VPC flow logs and metric collection

## Project Goals
- Deploy a web application in a cloud environment
- Automate server setup using Bash scripting
- Use S3 as the content source for the website
- Monitor system and networking activity in AWS
- Showcase a practical DevOps architecture for a simple application

## Repository Structure

- html-web-app/ - front-end website assets
  - index.html - main landing page
  - css/ - stylesheet files
  - js/ - JavaScript and slider dependencies
  - images/ - branding and UI assets
  - WEB-INF/web.xml - Java web configuration file
- VPC Architecture/ - AWS network and monitoring configuration files
  - script.sh - instance bootstrap and configuration script
  - flow-logs.json - IAM policy for VPC Flow Logs
  - flow-logs-trusted.json - trust policy for flow log role
  - memory_metrics.json - CloudWatch log permissions for memory metrics
  - s3-policy.json - read policy for S3 bucket access

## Web Application
The frontend is a static business website styled as a company portal for DevOpsRealtime. It includes:
- a top header with contact details and social links
- a multi-level navigation menu for company, services, technologies, solutions, and industry verticals
- a responsive layout with slider and business-oriented sections
- a contact page and supporting website assets

This application is not a full Java application in the traditional sense; it is mostly static content served over HTTP and designed to mimic a corporate marketing website.

## AWS Deployment Flow
The bootstrap script in VPC Architecture/script.sh automates the deployment process on EC2. It performs the following actions:

1. Detects the operating system (Amazon Linux or Ubuntu)
2. Installs required packages such as Apache/httpd, AWS CLI, and curl
3. Downloads the website file from an S3 bucket
4. Starts and enables the web server
5. Installs and configures the Amazon CloudWatch Agent
6. Validates system health, network connectivity, and S3 access

The design demonstrates a typical EC2 + S3 + CloudWatch architecture where static content is stored centrally and the instance is configured as a web server.

## Monitoring and Security Configuration
The JSON files in the VPC Architecture folder show how AWS services can be configured for observability and access control:

- flow-logs.json - grants permissions for VPC Flow Logs to publish to CloudWatch Logs
- flow-logs-trusted.json - defines the trust relationship required for the flow log service to assume a role
- memory_metrics.json - grants permissions for memory-related metrics logging
- s3-policy.json - allows read access to a specific S3 bucket

These files illustrate the infrastructure side of the project: collecting traffic logs, enabling visibility into VPC activity, and giving services the least required access.

## Tech Stack
- HTML, CSS, JavaScript
- Apache HTTP Server
- Bash scripting
- AWS EC2
- AWS S3
- AWS IAM
- Amazon CloudWatch
- VPC Flow Logs

## Suggested Usage
To use this project as a learning/demo environment:

1. Create an S3 bucket and upload the website content from html-web-app
2. Launch an EC2 instance with either Amazon Linux or Ubuntu
3. Run the bootstrap script from VPC Architecture/script.sh
4. Confirm that Apache is serving the page and CloudWatch is collecting logs
5. Review VPC flow logs and other AWS monitoring outputs for activity tracking

## Notes
This repository is intended as a practical DevOps example rather than a production-grade system. It is best suited for learning infrastructure automation, static website hosting, and AWS observability patterns.

## License
This project is provided for educational and demonstration purposes.
