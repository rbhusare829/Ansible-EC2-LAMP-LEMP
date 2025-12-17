# Ansible-EC2-LAMP-LEMP
# 🚀 LAMP on Target Server using Ansible

This project demonstrates how to **automatically install and configure a LAMP stack (Linux, Apache, MariaDB, PHP)** on a **target server** using **Ansible**. The deployment also includes serving a custom `index.html` page to verify successful setup.

---
![](./img/flow%20diagram.png)
## 🧩 Project Overview

This repository contains **two server automation projects using Ansible**:

1. **LAMP on Target Server**
   Linux + Apache + MariaDB + PHP
2. **LEMP on Target Server**
   Linux + NGINX + MariaDB + PHP (PHP-FPM)

Both projects demonstrate real-world **DevOps automation** by configuring complete web stacks on target servers using Ansible playbooks.

---

## 🧩 Project Overview

Using this Ansible playbook, you can:

* Remove **NGINX** if it exists
* Install **Apache (httpd)**, **MariaDB**, **PHP**, and **PHP-FPM**
* Start and enable required services
* Deploy a custom `index.html` file

This is ideal for **DevOps practice**, **server automation**, and **infrastructure configuration management**.

---

## 🏗️ Architecture

```
Local Machine (Ansible Controller)
        |
        |  SSH (Ansible)
        v
Target EC2 / Linux Server
        |
        ├── Apache (httpd)
        ├── MariaDB
        ├── PHP + PHP-FPM
        └── index.html (Web Page)
```

---

## 📁 Project Structure

```
ANSIBLE/
├── inventory.ini
├── lamp_on_target.yml      # LAMP stack automation
├── lemp_on_target.yml      # LEMP stack automation
├── index.html              # Apache test page
├── info.php                # PHP test page (NGINX)
├── http_install.yml
├── nginx_install.yml
└── README.md
```

```
ANSIBLE/
├── inventory.ini
├── lamp_on_target.yml
├── index.html
├── http_install.yml
├── nginx_install.yml
└── README.md
```

---

## ⚙️ Prerequisites

* Ansible installed on controller node
* Target server (Amazon Linux / RHEL based)
* SSH key-based access to target server
* Python installed on target server

---

## 🛠️ Inventory File (`inventory.ini`)

```ini
[targetservers]
13.xxx.xxx.xxx ansible_user=ec2-user ansible_ssh_private_key_file=ansible.pem
```

---

## 📜 Main Playbook (`lamp_on_target.yml`)

### 🔹 LAMP Stack Automation

**Stack:** Linux + Apache + MariaDB + PHP

### What this playbook does:

1. Uninstalls **NGINX** if present
2. Installs:

   * httpd (Apache)
   * mariadb105-server
   * php
   * php-fpm
3. Starts and enables services
4. Copies `index.html` to `/var/www/html/`

---

## 📜 Main Playbook (`lemp_on_target.yml`)

### 🔹 LEMP Stack Automation

**Stack:** Linux + NGINX + MariaDB + PHP (PHP-FPM)

### What this playbook does:

1. Installs:

   * nginx
   * mariadb105-server
   * php
   * php-fpm
2. Starts and enables services:

   * nginx
   * mariadb
   * php-fpm
3. Deploys a PHP test page:

   * `/usr/share/nginx/html/info.php`
   * Displays `phpinfo()` output

---

### What this playbook does:

1. Uninstalls **NGINX** if present
2. Installs:

   * httpd
   * mariadb105-server
   * php
   * php-fpm
3. Starts and enables services
4. Copies `index.html` to `/var/www/html/`

---

## ▶️ How to Run the Playbook

### ▶️ Run LAMP Playbook

```bash
ansible-playbook -i inventory.ini lamp_on_target.yml
```

### ▶️ Run LEMP Playbook

```bash
ansible-playbook -i inventory.ini lemp_on_target.yml
```

```bash
ansible-playbook -i inventory.ini lamp_on_target.yml
```

---

## 🌐 Output Verification

### 🔹 LAMP Verification (Apache)

Open in browser:

```
http://<Target-Server-Public-IP>
```

Expected Output:

> **LAMP on Target Server**
> Linux + Apache + MariaDB + PHP
> Deployed using Ansible
> Server Status: Running

---

### 🔹 LEMP Verification (NGINX + PHP)

Open in browser:

```
http://<Target-Server-Public-IP>/info.php
```

You should see the **PHP Info page**, confirming PHP-FPM is working with NGINX.

After successful execution, open the browser:

```
http://<Target-Server-Public-IP>
```

You should see:

> **LAMP on Target Server**
> Linux + Apache + MariaDB + PHP
> Deployed using Ansible
> Server Status: Running

---

## ✅ Expected Result

* Apache service running
* MariaDB service running
* PHP enabled
* Web page accessible via browser

---

## 🧠 Key Learning

* Ansible Playbooks
* Package management using `dnf`
* Service handling using `systemd`
* Configuration automation
* Real-world DevOps workflow

---

## 📝 Notes

* Designed for **Amazon Linux / RHEL-based OS**
* Make sure port **80** is open in the Security Group
* Can be extended to include PHP info pages or database automation

---

## 🎯 Conclusion

This project showcases a **clean and optimized Ansible-based LAMP deployment** on a target server. It’s perfect for **DevOps portfolios**, **GitHub projects**, and **hands-on automation practice**.

---

### 👨‍💻 Author

**Rohit Bhusare**
DevOps | AWS | Ansible | Terraform

---

⭐ If you like this project, don’t forget to star the repository!
# Ansible-EC2-LAMP-LEMP
