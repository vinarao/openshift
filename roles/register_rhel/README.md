# rhel_register_node

## Description:

Subscribe a system to Red Hat, either directly or via a Satellite

_Note: Still work in progress_

## Behaviour:

**Feature:** Subscribe a system to Red Hat
- **Given** a VM of capable size and power is available
- **Given** the connection details to the VM are known
- **When** A new RHEL-system has been installed
- **Then** register it to Red Hat (or Satellite)
- **Then** attach subscriptions

## Configuration:

Common variables used by this role:

| Variable  | Description  | Example  | 
|---|---|---|
| **redhat_user** | Red Hat Username |  |
| **redhat_pass** | Red Hat Password | |
| **redhat_activationkey** | Red Hat Activation Key | |
| **redhat_organization_id** | Red Hat Organization ID |  |
| **redhat_pool_ids** | Red Hat Subscription Pool IDs |  |

_Note: Username/Password and Activation Key based registrations are mutually exclusive.

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Subscribe to Red Hat
  include_role:
    name: rhel_register_node
  vars:
    redhat_user: myuser
    redhat_password: myuser
```

Note: add common variables to the `vars` list as required.
