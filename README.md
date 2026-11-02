# AWS EC2 Web Server Deployment (Lab 001)

Deployed a custom static website on an Amazon EC2 instance running Amazon Linux 2023, using Nginx for web serving, a locked-down security group, and CloudWatch for infrastructure monitoring.

![Deployed Website](screenshots/deployed-webpage.png)

**Stack:** AWS EC2 · Amazon Linux 2023 · Nginx · CloudWatch · HTML

## Architecture

```text
Browser
   |
Internet
   |
Security Group (lab-001-ssh-access)
   |
EC2 Instance (lab-001-ec2)
   |
Nginx Web Server
   |
Custom HTML Website

CloudWatch monitors EC2 CPU utilisation.
```

## What I Built

1. Provisioned an EC2 `t3.micro` instance running Amazon Linux 2023.
2. Configured SSH access and public HTTP access through a security group.
3. Connected to the instance using SSH key-based authentication.
4. Installed and configured Nginx using `dnf` and `systemctl`.
5. Replaced the default Nginx page with a custom HTML website.
6. Verified public website access in a browser.
7. Created a CloudWatch alarm on CPU utilisation.

## Security Configuration

| Port | Protocol | Source | Purpose |
|---|---|---|---|
| 22 | SSH | My public IP (`/32`) | Remote administration |
| 80 | HTTP | `0.0.0.0/0` | Public website access |

- SSH inbound access is restricted to a single IPv4 address, so SSH is not exposed to the internet.
- HTTP is publicly accessible to serve the website.
- The security group is named `lab-001-ssh-access` but also holds the HTTP rule. AWS does not allow renaming a security group after creation, so future labs will use names that cover the full purpose.
- The SSH private key was stored locally and excluded from the repository.

## CloudWatch Monitoring

| Setting | Configuration |
|---|---|
| Alarm | `lab-001-high-cpu-alarm` |
| Metric | `CPUUtilization` |
| Threshold | Greater than 80% |
| Period | 5 minutes |
| Evaluation | 2 out of 2 datapoints |
| Notifications | Not configured |

The alarm monitors sustained high CPU utilisation. SNS email notifications are a planned improvement.

## Troubleshooting

- **Website connection timeout:** Checked the Nginx service status, verified port 80 was listening, reviewed the security group rules and tested connectivity with PowerShell's `Test-NetConnection`.
- **SSH key permissions:** Corrected Windows private-key file permissions using `icacls` before establishing the SSH connection.

Public IP addresses, account IDs and resource identifiers are redacted in the screenshots.

## Future Improvements

- Add SNS email notifications to the CloudWatch alarm.
- Configure HTTPS using a TLS certificate.
- Attach an Elastic IP so the public address survives a stop/start.
- Install the CloudWatch Agent for memory and disk monitoring.
- Automate infrastructure provisioning using Terraform.

## Security & Cleanup

Private keys, AWS credentials and account details are not stored in this repository.

---

**Project:** Lab 001, AWS EC2 Linux Web Server Deployment
**Focus:** Cloud infrastructure, Linux administration, networking and monitoring.
