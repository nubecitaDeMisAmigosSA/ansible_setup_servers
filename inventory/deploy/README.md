# Inventory Explanation

The inventory file defines the servers and groups for Ansible to manage. Here's a breakdown of the provided inventory file:

```yaml
all:
  hosts:
    nubecita.remote:
      ansible_host: nubecita.dev
  vars:
    ansible_user: runner
    timezone: "Europe/Madrid"

  children:
    hetzner:
      hosts:
        nubecita.remote:
          users:
            larry:
              sudo: true
              ssh_key: ""
            runner:
              sudo: true
              ssh_key: ""
```

## Structure and Components

- **all**: This is the top-level group that includes all hosts and variables.
  - **hosts**: Defines the individual servers.
    - **nubecita.remote**: The name of the server.
      - **ansible_host**: Specifies the actual hostname or IP address (nubecita.dev) that Ansible will connect to.
  - **vars**: Variables that apply to all hosts within the group.
    - **ansible_user**: The user Ansible will use to connect to the hosts.
    - **timezone**: The timezone setting for the hosts.
  - **children**: Groups of hosts within the top-level group.
    - **hetzner**: A subgroup under the `all` group.
      - **hosts**: Defines the individual servers within the `hetzner` group.
        - **nubecita.remote**: The same server as defined under the `all` group.
          - **users**: User-specific configurations for the server.
            - **larry**: User named larry with the following properties:
              - **sudo**: Grants sudo privileges.
              - **ssh_key**: Placeholder for the user's SSH key.
            - **runner**: User named runner with the following properties:
              - **sudo**: Grants sudo privileges.
              - **ssh_key**: Placeholder for the user's SSH key.

### How It Works

1. **Host Definitions**: The inventory defines a single server named `nubecita.remote`, reachable at `nubecita.dev`.
2. **Group Variables**: Variables like `ansible_user` and `timezone` are set at the `all` group level, applying to all hosts within this group.
3. **Children Groups**: The `hetzner` group is a subgroup of `all`, containing the same host `nubecita.remote`.
4. **User Configurations**: Within the `hetzner` group, user-specific settings are provided for `larry` and `runner`, including sudo privileges and SSH key placeholders.
