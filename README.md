# ansible_setup_servers

- [ansible\_setup\_servers](#ansible_setup_servers)
  - [Overview](#overview)
  - [Roles and Playbooks](#roles-and-playbooks)
    - [Basic Configuration](#basic-configuration)
    - [User Configuration](#user-configuration)
    - [Server Hardening](#server-hardening)
  - [Setup Instructions](#setup-instructions)
  - [Usage](#usage)

## Overview

This repository, contains Ansible playbooks and roles designed to automate the configuration, user setup, and hardening of your VPS. This aims to be a basic setup that will help you have your remote environment up and running in a few easy steps, if you're interested in a more complex `Home Lab` environment, you can check [this repo](https://github.com/LarryGF/terraHom) where we'll leverage more advanced use cases of `ansible`,`terraform` and `kubernetes` to achieve the goal.

## Roles and Playbooks

### Basic Configuration

The `basic` role handles fundamental server configurations, such as setting up DNS resolution and installing applications.

### User Configuration

The `users` role is responsible for setting up user accounts and their environments, including custom configuration files and templates.

### Server Hardening

The `harden` role focuses on security enhancements, including SSH configuration and the setup of security tools like Fail2Ban.

## Setup Instructions

- Steps `1` and `2` are only necessary if you want to use the included `Github Action` to manage the changes in a `gitops` way

1. **Generate SSH Key**

    ```sh
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```

   - Copy the private key and public key.
   - Set the private key as `ANSIBLE_PRIVATE_KEY` in your repository secrets.

2. **Create Repository Variables**
   - Add the following repository variables:
     - `ANSIBLE_USER`: Your Ansible user.
     - `TIMEZONE`: Your desired timezone.

3. **Inventory Setup**
   - Ensure your inventory file is correctly configured. The default inventory file is located at `inventory/deploy/hosts.yaml`.You can refer to the [Inventory README](inventory/deploy/README.md) for more info on how it works.

## Usage

To execute the playbook, run the following command:

```sh
ansible-playbook -i inventory/deploy/hosts.yaml servers.yml
```

This command will apply all the roles defined in `servers.yml` to the servers listed in the inventory file.
