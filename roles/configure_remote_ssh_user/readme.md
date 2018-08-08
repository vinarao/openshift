# Create Remote SSH User Role

Creates a remote ssh user to prepare the machine to be accessed by Ansible.

## Prerequisites

An SSH public key in the following location **<<user_home>>/.ssh/remote_user_rsa.pub**

## Role Variables

| Variable | Description | Default |
|---|---|---|
| remote_ssh_user | the name of the remote user to be configured. | ansible |

## How to create the SSH key pair

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```