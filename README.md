# Ansible Automation & Configuration Management

<p align="center">
  <img src="https://img.shields.io/badge/Ansible-Automation-EE0000?style=for-the-badge&logo=ansible&logoColor=white" />
  <img src="https://img.shields.io/badge/Linux-System%20Administration-FCC624?style=for-the-badge&logo=linux&logoColor=black" />
  <img src="https://img.shields.io/badge/Docker-Containerization-2496ED?style=for-the-badge&logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/YAML-Configuration-CB171E?style=for-the-badge&logo=yaml&logoColor=white" />
</p>

<p align="center">
  <b>Learning Infrastructure Automation with Ansible</b>
</p>

## 📌 About The Project

This repository contains my hands-on Ansible practice and automation configurations focused on Linux system administration, configuration management, and infrastructure automation.

The objective is to understand how Ansible simplifies repetitive administrative tasks by automating server configuration, managing remote hosts, executing playbooks, and organizing automation through reusable roles.

It includes inventory configurations, Ansible playbooks, and a dedicated Docker role for automating Docker-related tasks.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Ansible | Configuration management and automation |
| Linux | Server administration |
| YAML | Playbooks and configuration files |
| SSH | Secure remote server connectivity |
| Docker | Container management |
| Git & GitHub | Version control |

## 📂 Project Structure

```text
ansible-files/
│
├── inventoryfile/       # Ansible inventory configurations
│
├── playbooks/           # Ansible playbooks
│
├── roles/
│   └── docker/          # Reusable Docker automation role
│
└── README.md
```

## ⚙️ Prerequisites

Before getting started, make sure you have:

- Linux or macOS environment
- Python 3 installed
- Ansible installed
- SSH access to remote Linux servers
- Docker (for Docker-related tasks)

Verify installations:

```bash
python3 --version
ansible --version
ssh -V
docker --version
```

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/shashankcodes-10/ansible-files.git

cd ansible-files
```

### 2. Configure SSH Access

Ansible uses SSH to connect to remote Linux machines.

Generate an SSH key pair if required:

```bash
ssh-keygen -t rsa -b 4096
```

Copy the public key to the remote server:

```bash
ssh-copy-id username@SERVER_IP
```

Test SSH connectivity:

```bash
ssh username@SERVER_IP
```

### 3. Configure Inventory

Navigate to the inventory directory:

```bash
cd inventoryfile
```

Ansible inventory defines the hosts and groups against which automation tasks are executed.

Example inventory:

```ini
[webservers]
server1 ansible_host=192.168.1.10
server2 ansible_host=192.168.1.11

[webservers:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=~/.ssh/id_rsa
```

Replace the example IP addresses and SSH configuration with your actual server details.

### 4. Verify Host Connectivity

From the repository root, execute:

```bash
ansible all -i inventoryfile/ -m ping
```

The ping module verifies whether Ansible can connect to the configured hosts and execute a module.

### 5. Execute Ansible Playbooks

Navigate to the playbooks directory:

```bash
cd playbooks
```

Execute a playbook:

```bash
ansible-playbook -i ../inventoryfile/ <playbook-name>.yml
```

Replace `<playbook-name>.yml` with the actual playbook filename.

### 6. Execute Docker Role

The repository contains a dedicated Docker role:

```text
roles/docker/
```

Ansible roles help organize automation into reusable components.

Example playbook structure for using the Docker role:

```yaml
---
- name: Configure Docker on Linux servers
  hosts: all
  become: true

  roles:
    - docker
```

Execute the playbook:

```bash
ansible-playbook -i inventoryfile/ <docker-playbook>.yml
```

Use the actual playbook that references the Docker role.

## 📚 Important Ansible Commands

### Inventory Commands

```bash
# Display inventory
ansible-inventory -i inventoryfile/ --list

# Display inventory in graph format
ansible-inventory -i inventoryfile/ --graph

# Test connectivity
ansible all -i inventoryfile/ -m ping
```

### Ad-hoc Commands

```bash
# Check remote uptime
ansible all -i inventoryfile/ -m command -a "uptime"

# Check disk usage
ansible all -i inventoryfile/ -m command -a "df -h"

# Check memory usage
ansible all -i inventoryfile/ -m command -a "free -h"

# Check operating system
ansible all -i inventoryfile/ -m command -a "uname -a"
```

### Playbook Commands

```bash
# Execute playbook
ansible-playbook -i inventoryfile/ playbooks/<playbook-name>.yml

# Syntax validation
ansible-playbook --syntax-check playbooks/<playbook-name>.yml

# Dry run
ansible-playbook -i inventoryfile/ playbooks/<playbook-name>.yml --check

# Execute with verbose output
ansible-playbook -i inventoryfile/ playbooks/<playbook-name>.yml -v
```

## 🔍 Understanding Ansible Architecture

```text
             Control Node
                  |
                  |
             Ansible Engine
                  |
             SSH Connection
                  |
        ---------------------
        |         |         |
        v         v         v
      Host 1    Host 2    Host 3
        |         |         |
        v         v         v
     Tasks     Tasks     Tasks
        |         |         |
        ---------------------
                  |
                  v
        Desired Configuration
```

**Key Components:**

- **Control Node:** Machine from which Ansible commands and playbooks are executed.
- **Inventory:** Defines the managed hosts.
- **Playbooks:** YAML files that describe automation tasks.
- **Modules:** Individual units of work executed by Ansible.
- **Roles:** Reusable and organized collections of automation tasks.
- **Tasks:** Individual operations performed on managed hosts.
- **Handlers:** Tasks triggered when notified by other tasks.
- **SSH:** Secure communication between the control node and managed hosts.

## 🔐 Security Best Practices

- Use SSH key-based authentication.
- Never commit private SSH keys.
- Store passwords and sensitive variables securely using Ansible Vault.
- Use `become` only when elevated privileges are required.
- Restrict SSH access to trusted IP addresses.
- Follow the principle of least privilege.
- Avoid storing credentials directly inside playbooks.

## 🎯 Learning Objectives

Through this repository, I am developing practical knowledge of:

- Ansible architecture and components.
- Inventory management.
- Ad-hoc commands and modules.
- YAML-based playbook development.
- Remote server configuration.
- SSH-based automation.
- Ansible roles and reusable configurations.
- Docker automation using Ansible.
- Linux system administration.
- Infrastructure automation concepts.

## 📖 Official Documentation

- [Ansible Documentation](https://docs.ansible.com/)
- [Ansible Playbooks](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html)
- [Ansible Inventory](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html)
- [Ansible Roles](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html)
- [Ansible Vault](https://docs.ansible.com/ansible/latest/vault_guide/index.html)

## 👨‍💻 Author

**Shashank Pipal**

Aspiring Cloud & DevOps Engineer

- GitHub: [@shashankcodes-10](https://github.com/shashankcodes-10)
- LinkedIn: [Connect with me](https://www.linkedin.com/in/shashank-pipal/)

---

<p align="center">
  ⭐ If you find this repository useful, consider giving it a star!
</p>

<p align="center">
  <b>Learn | Automate | Configure | Scale 🚀</b>
</p>
