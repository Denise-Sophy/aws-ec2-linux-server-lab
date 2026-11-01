# AWS EC2 Linux Web Server Deployment

A hands-on AWS project demonstrating how to provision a Linux server, deploy a custom website using Nginx, and monitor infrastructure using Amazon CloudWatch.

## Project Overview

Deployed a publicly accessible static website on an Amazon EC2 instance running Amazon Linux 2023.

**Technologies:** AWS EC2 · VPC · Security Groups · EBS · CloudWatch · Linux · Nginx · SSH · HTML

## Architecture & Configuration

| Component | Configuration |
|---|---|
| Region | us-east-1 |
| Instance | EC2 t3.micro |
| Operating System | Amazon Linux 2023 |
| Storage | 8 GiB encrypted gp3 |
| Web Server | Nginx |
| Remote Access | SSH |
| Web Traffic | HTTP (port 80) |
| Monitoring | Amazon CloudWatch |

## What I Built

1. **Provisioned an EC2 instance** running Amazon Linux 2023.
2. **Configured network security** with SSH restricted to my IP and public HTTP access.
3. **Connected through SSH** using a locally stored key pair.
4. **Explored Linux** using commands for system information, memory, disk and uptime.
5. **Installed and configured Nginx** as the web server.
6. **Deployed a custom HTML webpage** accessible over the internet.
7. **Configured CloudWatch monitoring** and a CPU alarm for utilisation above 80% across two consecutive five-minute periods.

## Screenshots

Project screenshots will be added here.

## Key Learnings

- Provisioning and accessing cloud infrastructure.
- Configuring security groups and network access.
- Administering a Linux server.
- Deploying a website using Nginx.
- Monitoring EC2 metrics and configuring CloudWatch alarms.
- Troubleshooting connectivity between cloud networking and application services.

## Future Improvements

- Configure HTTPS.
- Collect memory and disk metrics using CloudWatch Agent.
- Create a CloudWatch dashboard.
- Automate infrastructure provisioning with Terraform.

## Security Notes

SSH was restricted to my public IP. Private keys and AWS credentials are not included in this repository.

This is a foundational learning project, not a production-hardened deployment.
