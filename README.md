# AWS EC2 Linux Web Server

Deployed and configured a Linux web server on AWS EC2, hosting a custom static webpage using Nginx and monitoring instance performance with CloudWatch.

**Technologies:** AWS EC2 | Amazon Linux 2023 | Linux | Nginx | VPC | Security Groups | EBS | CloudWatch

## Architecture

Browser → Internet → Security Group → EC2 Instance → Nginx → Custom HTML Website

CloudWatch monitors EC2 performance metrics independently.

## Implementation

- Provisioned a `t3.micro` EC2 instance with an encrypted 8 GiB gp3 volume.
- Configured SSH access restricted to my public IP and HTTP access on port 80.
- Connected to the instance using SSH key-based authentication.
- Installed and managed Nginx using `dnf` and `systemctl`.
- Deployed a custom HTML webpage.
- Inspected Linux memory, disk usage, uptime and system information.
- Configured a CloudWatch CPU alarm for utilisation above 80% across two consecutive five-minute periods.

## Security Configuration

| Access | Port | Source |
|---|---:|---|
| SSH | 22 | My public IP (/32) |
| HTTP | 80 | 0.0.0.0/0 |



## Screenshots

Add evidence of the running EC2 instance, security group rules, Nginx service, deployed webpage and CloudWatch alarm.

## Future Improvements

HTTPS, CloudWatch Agent, SNS notifications and infrastructure automation using Terraform.

