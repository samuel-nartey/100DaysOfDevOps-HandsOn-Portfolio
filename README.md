# Linux Server Setup & Hardening

## Purpose
This project demonstrates the process of provisioning a Linux server, securing it against common threats, and configuring essential services for production-readiness.  
It’s a practical application of Linux administration skills — from user management and firewall setup to SSH hardening and system monitoring.

## Real-World Use Case
Companies hosting applications on cloud VMs or bare-metal servers must ensure their infrastructure is secure and stable.  
This setup could be applied to:
- Securing a web server hosting customer data
- Preparing a staging environment for developers
- Locking down cloud instances to meet compliance requirements (ISO 27001, SOC 2)

## Architecture Diagram
+-----------------------------+
| Client PC |
+-----------------------------+
|
SSH (Port 22)
|
+-----------------------------+
| Linux Server |
| - User Accounts & Groups |
| - SSH Key Authentication |
| - UFW Firewall |
| - Fail2ban |
| - Auditd |
+-----------------------------+

markdown
Copy
Edit

## Steps to Implement
1. **Provision Server**
   - Launch an Ubuntu 22.04 LTS VM on AWS EC2.
   - Update system packages (`sudo apt update && sudo apt upgrade -y`).

2. **User Management**
   - Create a non-root admin user:  
     ```bash
     sudo adduser devops_admin
     sudo usermod -aG sudo devops_admin
     ```

3. **SSH Hardening**
   - Configure SSH key-based login.
   - Disable root login and password authentication in `/etc/ssh/sshd_config`.

4. **Firewall Setup**
   - Allow SSH & HTTP:  
     ```bash
     sudo ufw allow 22
     sudo ufw allow 80
     sudo ufw enable
     ```

5. **Intrusion Prevention**
   - Install and configure Fail2ban.
   - Enable Auditd to log system events.

6. **Monitoring & Logging**
   - Install htop, sysstat, and logwatch.
   - Schedule regular reports via cron.

## Configuration Files & Scripts
- `sshd_config` – Modified to disable root login & enforce key authentication.
- `ufw-rules.sh` – Script to apply firewall rules.
- `fail2ban/jail.local` – Custom ban rules for SSH brute-force prevention.

## Logs & Troubleshooting
- Encountered SSH lockout after disabling password auth without uploading keys — resolved by using EC2 console to re-enable.
- UFW blocked HTTP traffic initially due to missing `sudo ufw allow 80`.

## Lessons Learned
- Always test new SSH configs in a separate session before closing the existing one.
- Security hardening is a balance between locking down services and maintaining usability.

## Why This Matters
Linux server security is foundational for all DevOps and cloud roles.  
This project demonstrates:
- Ability to work with cloud-hosted infrastructure.
- Understanding of production security best practices.
- Hands-on skills with Linux, networking, and automation scripts.