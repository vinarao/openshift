# network_manager

## Description:

Starts and enables NetworkManager service

_Note: This role is only needed for OpenShift nodes if nework was not configured using NetworkManager (On standard RHEL 7 it should not be needed).

## Behaviour:

**Feature:** Enables NetworkManager, sets all NetworkManager connections to start on boot, disables 'network' service.
**Given:** NetworkManager package is installed
**When:** Before deploying Openshift on the nodes without NeworkManager

## Configuration:

Common variables used by this role:

| Variable  | Description  | Example  | 
|---|---|---|
| **connections_to_ignore** | List of connections that should not autoconnect | |

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Enable NetworkManager
  include_role:
    name: network_manager
  vars:
    connections_to_ignore:
      - eth3
```

Note: add common variables to the `vars` list as required.
