# ansible-stuff
Playbooks to help me learn Ansible

# Usage

## Is this for me?
This isn't as extensive on config since it's for personal use. You will likely end up adding variables for Jinja templates.
That said, please feel free to try my playbooks out!

## Inventory
Copy `inventory.example.yaml` to `inventory.yaml`. It should look like this:

```yaml
main:
  hosts:
    server.example.com:
```

Where `server.example.com` is the hostname of your server.

For local testing, `inventory.local.yml` is also provided for use.

Then copy `vars.example.yaml` to `group_vars/main.yaml` and modify as needed.

Alternatively, variables can be kept in the inventory, and even set per-host:

```yaml
main:
  hosts:
    server.example.com:
      this_is_a_host_var: true
  vars:
    this_is_a_group_var: true
```

Full information on inventories is in the [Ansible documentation](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html).

## Running playbooks

Each subdirectory (forgejo, caddy, etc) has a playbook to install/configure/update a service.
So to run any of them:

```
ansible-playbook -Ki inventory service/playbook.yaml
```

Where `inventory` is your inventory file and `service` is the thing you want to install.

### Tags
Tags select certain tasks and save time during Ansible runs. When running playbooks add `--tags tag1,tag2,...`
to the command to use them.

Currently only the `config` tag exists, for configuration tasks.

### Playbook documentation

In each playbook directory there may be a README with more information like post-install steps.
