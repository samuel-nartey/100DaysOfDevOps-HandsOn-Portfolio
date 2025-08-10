# Day 1–2: Linux User Management (Hands-On)

## 📌 Objective
As part of the **100 Days of DevOps Hands-On Portfolio**, the goal for Day 1–2 is to practice **Linux user management** tasks:
- Create users with specific shell access rules.
- Set expiry dates for temporary accounts.
- Enforce security by disabling root SSH access.
- Manage file permissions to allow executable scripts.

---

## Vision
To build a practical, command-driven DevOps portfolio where every task is documented step-by-step, with clear examples and screenshots — so anyone can follow and reproduce the process.

---

## 🛠 Tasks

### 1️⃣ Create a user with a non-interactive shell
**Command:**
```bash
sudo useradd -s /sbin/nologin yousuf
Verify:


grep yousuf /etc/passwd
Example Output:


yousuf:x:1001:1001::/home/yousuf:/sbin/nologin
Screenshot:

2️⃣ Create a temporary user with an expiry date
Command:


sudo useradd -e 2023-12-07 john
Verify expiry date:


chage -l john
Example Output:


Account expires : Dec 07, 2023
