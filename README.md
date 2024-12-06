# System Automation with Ansible

This project automates the deployment of a web server and a database server using Ansible. The automation tasks include configuring firewalls, deploying web files, setting up MySQL databases, and more.

## Table of Contents
- [Description](#description)
- [Overview](#overview)	
- [Setup](#setup)
  - [Prerequisites](#prerequisites)
  - [Connect to Managed Nodes](#connect-to-managed-nodes)
  - [Inventory File](#inventory-file)
  - [Ansible Configuration](#ansible-configuration)
  - [Check connections](#check-connections)
- [Usage](#usage)
  - [Deploy Website](#deploy-website)
  - [Access Website via the Webserver IP](#access-website-via-the-webserver-ip)
- [Authors](#authors)

## Description

This is a project of Group 15 in class NT132.P11.ANTT, from the subject Networks and Systems Administration - NT132, at the University of Information Technology, Vietnam National University.

## Overview

This project demonstrates how to manage a simple system setup with:
- **Web Server**: Hosts a website, allowing HTTP and HTTPS traffic.
- **Database Server**: Manages a MySQL database for the web application.

The configuration supports:
- Firewall rules
- SELinux adjustments
- Remote MySQL access
- Automatic database import


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


## Usage

### Deploy Website
You may be asked for sudo password:
```
ansible-playbook global.yml --ask-become-pass
```

### Access Website via the Webserver IP
```
10.10.10.10
```


## Authors

Contributors names and contact info:
- Tran The Huu Phuc (22521143) - [@tranthehuuphuc](https://github.com/tranthehuuphuc)
- Tran Thi Thuy Vy (22521709) - [@vytr09](https://github.com/vytr09)
- Le Thi Bich Tuyen (22521630) - [@tuyen2201](https://github.com/tuyen2201)
- Ha Minh Quan (22521177) - [@HaMinhQuan-Uit](https://github.com/HaMinhQuan-Uit)


