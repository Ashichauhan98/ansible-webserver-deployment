# Automated Web Server Deployment using Ansible

## Project Overview

This project demonstrates infrastructure automation using Ansible and AWS EC2. The objective was to automate the deployment and configuration of Apache web servers across multiple Linux servers using a single Ansible playbook.

The setup consists of one Ansible Control Node and three Managed Nodes running on AWS EC2 instances. Communication between the servers is established securely using SSH key authentication.

---

## Architecture

* **1 Control Node (Ansible Master)**
* **3 Managed Nodes (Web Servers)**
* Secure communication using SSH
* Automated deployment using YAML playbooks

```
Local Machine
      |
      | SSH
      ↓
+-------------------+
| Ansible Master    |
| (Control Node)    |
+-------------------+
      |
      | Ansible Playbook Execution
      |
------------------------------------------------
|                     |                         |
↓                     ↓                         ↓
Web Server 1      Web Server 2            Web Server 3
(Managed Node)    (Managed Node)          (Managed Node)
```

---

## Technologies Used

* AWS EC2
* Ansible
* YAML
* Ubuntu Linux
* Apache Web Server
* SSH

---

## Features

* Automated web server installation.
* Automated Apache service configuration.
* Deployment across multiple servers simultaneously.
* SSH-based secure communication.
* Reduced manual server configuration effort.

---

## Project Workflow

### Step 1

Launch four EC2 instances:

* 1 Control Node
* 3 Managed Nodes

### Step 2

Configure Security Groups to allow:

* SSH (Port 22)
* HTTP (Port 80)

### Step 3

Install Ansible on the Control Node.

### Step 4

Configure passwordless SSH communication between Control Node and Managed Nodes.

### Step 5

Create an inventory file containing managed node details.

### Step 6

Create an Ansible playbook using YAML.

### Step 7

Execute the playbook:

```bash
ansible-playbook -i inventory webserver.yml
```

### Step 8

Verify successful deployment through browser access.

---

## Inventory File

```ini
[webservers]
web1 ansible_host=<managed-node-1-ip>
web2 ansible_host=<managed-node-2-ip>
web3 ansible_host=<managed-node-3-ip>

[webservers:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=/path/to/private-key.pem
```

---

## Playbook Tasks

The playbook performs the following operations:

1. Gather system information.
2. Update package repositories.
3. Install Apache Web Server.
4. Start and enable Apache service.
5. Deploy a custom HTML page.

---

## Ansible Connectivity Verification

```bash
ansible webservers -i inventory -m ping
```

Expected Result:

```text
web1 | SUCCESS => pong
web2 | SUCCESS => pong
web3 | SUCCESS => pong
```

---

## Project Results

* Successfully deployed Apache web servers on three EC2 instances.
* Achieved centralized configuration management.
* Reduced manual setup effort through automation.
* Demonstrated infrastructure as code concepts.

---

## Screenshots

### EC2 Instances

* Control Node
* Managed Nodes

### Successful Ansible Ping

* Verification of connectivity between nodes.

### Playbook Execution

* Successful execution of all tasks.

### Web Server Output

* Apache web page running successfully on all managed nodes.

---

## Learning Outcomes

Through this project, I gained hands-on experience with:

* Infrastructure Automation
* Configuration Management
* Ansible Playbooks
* AWS EC2
* Linux Administration
* SSH Authentication
* Multi-Server Deployment

---

## Author

**Ashi Chauhan**
