# ansible-stuff
Playbooks to help me learn Ansible

# Usage

## Is this for me?
This isn't as extensive on config since it's for personal use. You will likely end up adding variables for Jinja templates.
That said, please feel free to try my playbook out!

## Inventory
First, [set up your inventory](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html).
It should at least look like this:
```yaml
ungrouped:
  hosts:
    server.example.com:
```

Where `server.example.com` is the hostname of your server.

For local testing, `inventory.local.yml` is provided to quickly get started.

Then make the `host_vars` directory, and copy `vars.yaml` to `host_vars/NAME_OF_YOUR_HOST.yaml`
(e.g. `host_vars/server.example.com.yaml` or `host_vars/localhost.yaml`). Be sure to set `base_domain` inside it!

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
