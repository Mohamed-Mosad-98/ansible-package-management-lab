# Package Management Commands

## Verify Connectivity

```bash
ansible servers -i inventory/inventory.ini -m ping
```

---

## Gather OS Information

```bash
ansible servers -i inventory/inventory.ini -m setup -a "filter=ansible_distribution*"
```

---

# Apache Package Management

## Install Apache

```bash
ansible servers -i inventory/inventory.ini \
-m apt \
-a "name=apache2 state=present update_cache=yes" \
-b -K
```

## Verify Apache Package

```bash
ansible servers -i inventory/inventory.ini \
-m shell \
-a "dpkg -l | grep apache2"
```

## Check Apache Version

```bash
ansible servers -i inventory/inventory.ini \
-m command \
-a "apache2 -v"
```

## Remove Apache

```bash
ansible servers -i inventory/inventory.ini \
-m apt \
-a "name=apache2 state=absent" \
-b -K
```

## Verify Apache Service

```bash
ansible servers -i inventory/inventory.ini \
-m command \
-a "systemctl is-active apache2"
```

---

# User Management

## Create DevOps User

```bash
ansible servers -i inventory/inventory.ini \
-m user \
-a "name=devopsuser state=present shell=/bin/bash" \
-b -K
```

## Verify User

```bash
ansible servers -i inventory/inventory.ini \
-m command \
-a "id devopsuser"
```

---

# Directory Management

## Create Directory

```bash
ansible servers -i inventory/inventory.ini \
-m file \
-a "path=/opt/devops state=directory owner=devopsuser group=devopsuser mode=0755" \
-b -K
```

## Verify Directory

```bash
ansible servers -i inventory/inventory.ini \
-m command \
-a "ls -ld /opt/devops"
```

---

# File Management

## Create File

```bash
ansible servers -i inventory/inventory.ini \
-m copy \
-a "content='Managed by Ansible' dest=/opt/devops/info.txt owner=devopsuser group=devopsuser mode=0600" \
-b -K
```

## Verify File

```bash
ansible servers -i inventory/inventory.ini \
-m command \
-a "ls -l /opt/devops/info.txt"
```

---

# Playbook Validation

## Syntax Check

```bash
ansible-playbook --syntax-check \
-i inventory/inventory.ini \
playbooks/package-management.yml
```

## Execute Playbook

```bash
ansible-playbook \
-i inventory/inventory.ini \
playbooks/package-management.yml
```

---

# Verify Installed Packages

## Git

```bash
ansible servers -i inventory/inventory.ini \
-m command \
-a "git --version"
```

## Curl

```bash
ansible servers -i inventory/inventory.ini \
-m command \
-a "curl --version"
```

## Wget

```bash
ansible servers -i inventory/inventory.ini \
-m command \
-a "wget --version"
```

## Nginx Service

```bash
ansible servers -i inventory/inventory.ini \
-m command \
-a "systemctl is-active nginx"
```

```bash
ansible servers -i inventory/inventory.ini \
-m command \
-a "systemctl is-enabled nginx"
```
