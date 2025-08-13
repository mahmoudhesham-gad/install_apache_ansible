# Role Name

install_apache

## Description

This role installs and enables the Apache web server (`apache2` on Debian-based systems, `httpd` on RedHat-based systems).

## Requirements

- SSH connection to the managed nodes must be established.
- It is recommended to use SSH key-based authentication and passwordless `sudo` for privilege escalation.

## Role Variables

The role uses OS-specific variables to determine the correct package name for Apache.

- `apache_name`: The name of the Apache package.
  - `vars/Debian.yml`: `apache_name: "apache2"`
  - `vars/RedHat.yml`: `apache_name: httpd`

The appropriate variable file is included automatically based on the `ansible_os_family` fact.

## Dependencies

This role has no dependencies on other roles.

## Example Playbook

Here is an example of how to use the `install_apache` role in a playbook:

```yaml
---
- hosts: webservers
  roles:
    - install_apache
```

## How to use

To execute the role, run the `ansible-playbook` command, specifying your inventory file and playbook.

For example, from the root directory of the project:

```bash
ansible-playbook -i hosts.ini playbook.yml
```
