# Ansible Package Management

This project demonstrates how to manage packages, users, directories, files, and services on multiple Ubuntu servers using **Ansible Ad-hoc Commands** and **Ansible Playbooks**.

---

## Lab Objectives

- Verify Ansible connectivity
- Gather remote host information
- Install and remove packages
- Manage system users
- Create directories and files
- Deploy applications using Playbooks
- Verify installed software and services

---

## Environment

| Component | Value |
|-----------|-------|
| Control Node | Ubuntu |
| Managed Nodes | Ubuntu 24.04 |
| Automation Tool | Ansible |
| Inventory | Static Inventory |

---

# Repository Structure

```text
ansible-package-management/
│
├── inventory/
│   └── inventory.ini
│
├── playbooks/
│   └── package-management.yml
│
├── commands/
│   └── package-management-commands.md
│
├── screenshots/
│   ├── 01-ansible-ping.png
│   ├── 02-create-devops-user.png
│   ├── 03-create-devops-directory.png
│   ├── 04-install-apache.png
│   ├── 05-apache-version.png
│   ├── 06-remove-apache.png
│   ├── 07-apache-inactive.png
│   ├── 08-playbook-syntax-check.png
│   ├── 09-playbook-execution.png
│   ├── 10-playbook-recap.png
│   └── 11-verify-installed-packages.png
│
└── README.md
```

---

# Inventory

```ini
[servers]
node1 ansible_host=192.168.75.139
node2 ansible_host=192.168.75.140

[servers:vars]
ansible_user=xubuntu
ansible_python_interpreter=/usr/bin/python3
```

---

# Playbook

The playbook performs the following tasks:

- Remove Apache
- Install Git
- Install Curl
- Install Wget
- Install Nginx
- Enable and start Nginx
- Create `devopsuser`
- Create `/opt/devops`
- Create `info.txt`

---

# Verification

## 1. Verify Connectivity

```bash
ansible servers -i inventory/inventory.ini -m ping
```

<img width="1920" height="1080" alt="01-ansible-ping" src="https://github.com/user-attachments/assets/14de970f-1e24-451e-a733-9ecc39627d50" />

---

## 2. Create DevOps User

```bash
ansible servers -m user ...
```

<img width="1920" height="1080" alt="02-create-devops-user" src="https://github.com/user-attachments/assets/28a6ed5f-9616-4fba-bdb3-1e02ee834b32" />


---

## 3. Create DevOps Directory

```bash
ansible servers -m file ...
```

<img width="1920" height="1080" alt="03-create-devops-directory" src="https://github.com/user-attachments/assets/4d9b69b7-a5af-4bc1-93c3-931d600d30b6" />


---

## 4. Install Apache

```bash
ansible servers -m apt ...
```

<img width="1920" height="1080" alt="04-install-apache" src="https://github.com/user-attachments/assets/c511c0e6-684d-431e-9ba5-601de2fb339d" />


---

## 5. Verify Apache Version

```bash
apache2 -v
```

<img width="1135" height="240" alt="05-apache-version" src="https://github.com/user-attachments/assets/d934e842-cf6e-48fd-80da-58f79af60929" />


---

## 6. Remove Apache

```bash
state=absent
```

<img width="1920" height="1080" alt="06-remove-apache" src="https://github.com/user-attachments/assets/a5ad8bd1-236e-4b28-86d4-683113ceb218" />

---

## 7. Verify Apache Removal

```bash
systemctl is-active apache2
```

<img width="1218" height="687" alt="07-apache-inactive" src="https://github.com/user-attachments/assets/38bc626f-4e38-4b42-8f16-c1139c7344e1" />

---

## 8. Validate Playbook

```bash
ansible-playbook --syntax-check
```

<img width="1197" height="408" alt="08-playbook-syntax-check" src="https://github.com/user-attachments/assets/9b3f447e-73e0-4df6-a1c4-eb96aac1d41f" />


---

## 9. Execute Playbook

```bash
ansible-playbook package-management.yml
```

<img width="1233" height="547" alt="09-playbook-execution" src="https://github.com/user-attachments/assets/cab81f04-ed8c-4ad1-b841-f75dd029d588" />

---

## 10. Play Recap

Successful execution on both managed nodes.

<img width="1328" height="468" alt="10-playbook-recap" src="https://github.com/user-attachments/assets/f9867da5-75ca-4b65-9d46-5e195a5bd189" />

---

## 11. Verify Installed Packages

```bash
git --version
curl --version
wget --version
```

<img width="1328" height="486" alt="11-verify-installed-packages" src="https://github.com/user-attachments/assets/6fdfbe06-41d1-45fe-9fa5-6da671e616ab" />

---

# Commands

All commands used during this lab are available in:

```
commands/package-management-commands.md
```

---

# Skills Demonstrated

- Ansible Inventory
- Ad-hoc Commands
- Playbooks
- Package Management
- User Management
- File Management
- Directory Management
- Service Management
- YAML
- Linux Administration

---

# Author

**Mohamed Mosad Fahmy**

- GitHub: https://github.com/Mohamed-Mosad-98
- LinkedIn: https://linkedin.com/in/mohamed-mosad-516aa717b
