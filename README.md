# comp350-ansible-for-containers
This project focuses on creating a **containerized web application** orchestrated through **Docker Compose**. The application consists of four containers and demonstrates fundamental DevOps principles such as container orchestration, networking, and persistence.
# COMP 350: Introduction to DevOps  
## Project 2: Ansible Configuration Management with Docker Compose  

**Due Date:** June 7, 2024  
**Instructor:** Hakan Ayral, Spring 2024  
**TA Contact:** Javid Baydamirli - [jbaydamirli21@ku.edu.tr](mailto:jbaydamirli21@ku.edu.tr)  
**GitHub Classroom Link:** [https://classroom.github.com/a/nuHyAiLl](https://classroom.github.com/a/nuHyAiLl)

---

## Overview

This project demonstrates the use of **Ansible** for configuration management within a **Docker Compose** environment. The setup includes three containers: one control node and two managed nodes. An Ansible playbook is used to configure and deploy Nginx on the managed nodes.

---

## Project Requirements

### Docker Compose Environment

1. **Images and Containers**:
   - **Control Node (1 container)**:
     - Contains Ansible and all required configurations.
   - **Managed Nodes (2 containers)**:
     - Serve as the inventory for the control node.

2. **Control Node Configuration**:
   - Contains:
     - Python
     - SSH client
     - Ansible (pre-installed and configured)
     - Ansible playbook
     - Inventory file (points to the managed nodes)
     - SSH key pair (private and public keys)
     - Ansible configuration file (properly set up to reference the inventory and SSH key)
     - A shell as the main process.

3. **Managed Nodes Configuration**:
   - Contains:
     - Python
     - SSH server (OpenSSH)
     - Public key for SSH
     - A shell as the main process.
   - Exposes:
     - SSH port mapped to the host.
     - Port 80 mapped to the host (even without a web server initially).

4. **Persistent Shells**:
   - All containers should have a running shell as the main process.

---

### Ansible Playbook

The playbook should:
1. **Install Nginx**: Use `apt` to install the Nginx web server on the managed nodes.
2. **Configure Nginx**:
   - Create a virtual host file in `/etc/nginx/sites-enabled/` to serve a static web page.
3. **Serve Static Content**:
   - Create an `index.html` file at the location specified in the virtual host file.

---

## Expected Behavior

1. **Initial State**:
   - Running `docker-compose up` should start all three containers with their respective configurations:
     - Managed nodes should have SSH and shell running, but no Nginx or static files.
     - Control node should have the shell running.
2. **Post-Playbook Execution**:
   - Running the playbook from the control node should result in:
     - Both managed nodes having Nginx installed and serving the `index.html` file via port 80.
   - The static web page should be accessible from the host.

---

## Setup and Usage

### Prerequisites

- **Docker** and **Docker Compose** installed.
- Clone the project from the [GitHub Classroom repository](https://classroom.github.com/a/nuHyAiLl).

### Steps

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
