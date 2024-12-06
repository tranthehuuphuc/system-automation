# System Automation
## Group 15 - NT132.P11.ANTT - University of Information Technology 2023-2024

# System Automation with Ansible

This project automates the deployment of a web server and a database server using Ansible. The automation tasks include configuring firewalls, deploying web files, setting up MySQL databases, and more.

## Table of Contents
1. [Overview](#overview)
2. [Setup](#setup)
3. [Usage](#usage)
5. [Roles and Responsibilities](#roles-and-responsibilities)
7. [Troubleshooting](#troubleshooting)

---

## Overview

This project demonstrates how to manage a simple system setup with:
- **Web Server**: Hosts a website, allowing HTTP and HTTPS traffic.
- **Database Server**: Manages a MySQL database for the web application.

The configuration supports:
- Firewall rules
- SELinux adjustments
- Remote MySQL access
- Automatic database import

---

## Setup

### Prerequisites
- Ansible installed on the **Control Node**.
- CentOS 9 or later installed on Managed Nodes.
- SSH access from the Control Node to all Managed Nodes.

### Connect to Managed Nodes
- Generate keypair (Enter to default)
```
ssh-keygen -t ed25519 -C <your_username>
```
- Copy public key to all Managed Nodes (Public key file in the same directory with Private key file)
```
ssh-copy-id -i ~/.ssh/id_ed25519.pub <Managed Node IP>
```

### Inventory File
Update the `inventory` file with the IPs of the servers:
```
[webserver]
10.10.10.10

[dbserver]
10.10.10.20
```

### Ansible Configuration
Update the `ansible.cfg` file with the path of Private key file:
```
[defaults]
inventory = ./inventory
private_key_file = ~/.ssh/id_ed25519
```

### Check connections
```
ansible all -m ping
```

---

## Usage

### Deploy Website
You may be asked for sudo password:
```
ansible-playbook global.yml --ask-become-pass
```

### Access Website with the Webserver IP
```
10.10.10.10
```

---


