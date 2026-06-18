# ansible-stuff
Playbooks to help me learn Ansible

# Usage

## Is this for me?
This isn't as extensive on config since it's for personal use. You will likely end up adding variables for Jinja templates.
That said, please feel free to try my playbook out!

## Inventory
First, [set up your inventory](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html).

```yaml
all:
  vars:
    base_domain: example.com # Base domain for everything

# Group for every host running Caddy
caddy:
  hosts:
    caddy_host:
  vars:
    caddy:
      self_sign: false # Should Caddy use an internal CA?

# Group for every host running Forgejo
forgejo:
  hosts:
    forgejo_host:
  vars:
    forgejo:
      name: "Forgejo"
      slogan: "Internal test forge"
      domain: "git.{{ base_domain }}"
```

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
