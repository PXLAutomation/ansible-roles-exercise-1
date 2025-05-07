# Firewall Configuration with Ansible

This project demonstrates how to use Ansible roles and variables to efficiently configure firewall rules on different types of servers.

## Project Structure

```
firewall-project/
├── ansible.cfg          # Ansible configuration
├── site.yml             # Main playbook
├── inventory/           # Inventory directory
│   ├── hosts            # Host definitions
│   └── group_vars/      # Group variables
│       ├── all.yml      # Variables for all hosts
│       ├── webservers.yml # Variables for web servers
│       └── dbservers.yml # Variables for database servers
└── roles/
    └── firewall/        # Firewall configuration role
```

## How to Run

1. Update the inventory/hosts file with your actual server information
2. Run the playbook:

```bash
ansible-playbook site.yml
```

3. To run with additional options:

```bash
# Dry run (check mode)
ansible-playbook site.yml --check

# Run only for web servers
ansible-playbook site.yml --limit webservers

# Run only installation tasks
ansible-playbook site.yml --tags install
```

## Role Variables

The firewall role uses variables from group_vars to determine which ports to open:

- **common_firewall_ports**: Applied to all servers (SSH)
- **specific_firewall_ports**: Applied based on server type (HTTP/HTTPS for web servers, MySQL for database servers)

## Verification

After running the playbook, the current firewall configuration will be displayed. You can also check manually on any server:

```bash
firewall-cmd --list-all
```
