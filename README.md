# Ansible Playbooks

A collection of Ansible playbooks for server management and automation tasks.

## Structure

```
ansible-playbooks/
├── plays/
│   └── playbook.yaml       # Main playbook with webserver tasks
├── tasks/
│   └── task_apt_upgrade_packages.yaml  # APT package management tasks
└── README.md
```

## Playbooks

### Main Playbook (`plays/playbook.yaml`)

Contains two main plays:

1. **Ping Webservers** - Basic connectivity test for webserver hosts
2. **Upgrade Packages** - Updates and upgrades packages on webservers using APT

## Tasks

### APT Package Upgrade (`tasks/task_apt_upgrade_packages.yaml`)

Performs comprehensive package management:
- Updates package cache
- Safely upgrades packages
- Removes unused packages (autoremove)
- Cleans package cache (autoclean)

## Usage

### Prerequisites

- Ansible installed on control machine
- SSH access to target hosts
- Inventory file with `webservers` group defined

### Running Playbooks

```bash
# Run the main playbook
ansible-playbook -i inventory plays/playbook.yaml

# Run with specific hosts
ansible-playbook -i inventory plays/playbook.yaml --limit webserver1

# Check mode (dry run)
ansible-playbook -i inventory plays/playbook.yaml --check
```

### Inventory Example

Create an inventory file with your webservers:

```ini
[webservers]
webserver1 ansible_host=192.168.1.10
webserver2 ansible_host=192.168.1.11
```

## Requirements

- Target hosts must be Debian/Ubuntu-based systems (uses APT)
- Sudo privileges required for package management tasks