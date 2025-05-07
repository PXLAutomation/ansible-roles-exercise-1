# Ansible Role Exercise: Firewall Configuration

## Objective
Create a structured Ansible project that uses roles and variables to configure the firewall on different types of servers.

## Starting Requirements
* 2 RHEL/AlmaLinux machines
* Ansible installed on your control node

## Project Structure
Create a complete Ansible project with the following structure:

```
firewall-project/
├── ansible.cfg
├── site.yml
├── inventory/
│   ├── hosts
│   └── group_vars/
│       ├── all.yml
│       ├── webservers.yml
│       └── dbservers.yml
└── roles/
    └── firewall/
        ├── tasks/
        │   └── main.yml
        ├── handlers/
        │   └── main.yml
        └── defaults/
            └── main.yml
```

## Tasks

### 1. Initialize the Project Structure
* Create the directory structure above
* Initialize the `firewall` role using `ansible-galaxy init roles/firewall`

### 2. Inventory Setup
* Create an inventory directory with a hosts file
* Define two host groups: "webservers" and "dbservers"
* Create appropriate group_vars files for each group

### 3. Role Development
* Develop the `firewall` role to:
  * Install firewalld
  * Ensure firewalld is running and enabled
  * Configure appropriate firewall rules based on host group

### 4. Main Playbook (site.yml)
* Create a `site.yml` file at the project root
* Apply the firewall role to appropriate host groups
* Use variables to control which ports are opened on different servers

## Requirements

1. **Variables Setup:**
   * Define variables for firewall ports in group_vars files
   * Allow incoming traffic on port `80` on the webservers
   * Allow incoming traffic on port `3306` on the dbservers

2. **Role Implementation:**
   * The `firewall` role should handle all firewall configuration
   * Use conditionals to apply the correct rules based on the server type
   * Include appropriate handlers for service restart

3. **Efficiency Requirement:**
   * No repeating tasks - use a single role with variables
   * Use loop constructs when applying multiple similar firewall rules

## Bonus Tasks
* Add support for additional ports (SSH on port 22 for all servers)
* Implement a development inventory with different firewall settings
* Create a custom handler to validate firewall rules after applying them