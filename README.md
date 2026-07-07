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

![Ansible Ping](screenshots/01-ansible-ping.png)

---

## 2. Create DevOps User

```bash
ansible servers -m user ...
```

![Create User](screenshots/02-create-devops-user.png)

---

## 3. Create DevOps Directory

```bash
ansible servers -m file ...
```

![Directory](screenshots/03-create-devops-directory.png)

---

## 4. Install Apache

```bash
ansible servers -m apt ...
```

![Install Apache](screenshots/04-install-apache.png)

---

## 5. Verify Apache Version

```bash
apache2 -v
```

![Apache Version](screenshots/05-apache-version.png)

---

## 6. Remove Apache

```bash
state=absent
```

![Remove Apache](screenshots/06-remove-apache.png)

---

## 7. Verify Apache Removal

```bash
systemctl is-active apache2
```

![Apache Removed](screenshots/07-apache-inactive.png)

---

## 8. Validate Playbook

```bash
ansible-playbook --syntax-check
```

![Syntax Check](screenshots/08-playbook-syntax-check.png)

---

## 9. Execute Playbook

```bash
ansible-playbook package-management.yml
```

![Playbook Execution](screenshots/09-playbook-execution.png)

---

## 10. Play Recap

Successful execution on both managed nodes.

![Play Recap](screenshots/10-playbook-recap.png)

---

## 11. Verify Installed Packages

```bash
git --version
curl --version
wget --version
```

![Verification](screenshots/11-verify-installed-packages.png)

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
