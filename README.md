# ansible-stuff
Playbooks to help me learn Ansible

# Usage

## Inventory
First, [set up your inventory](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html).
If you're testing on your own machine, copy `inventory.local.ini` to `inventory.ini`.

The `base_domain` variable *must* be set. `inventory.local.ini` sets this to test.localhost.

## Running playbooks

Each subdirectory (forgejo, caddy, etc) has a playbook to install/configure/update a service.
So to run any of them:

```
ansible-playbook -Ki inventory service/playbook.yaml
```

Where `inventory` is your inventory file and `service` is the thing you want to install.