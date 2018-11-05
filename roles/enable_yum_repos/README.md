# rhel_enable_repos

## Description:

Enable required Red Hat repositories via subscription manager

_Note: Still work in progress_

## Behaviour:

**Feature:** Disable all enabled repositories and enable selected ones.

## Configuration:

Common variables used by this role:

| Variable  | Description  | Example  | 
|---|---|---|
| **repos_to_enable** | List of Red Hat repositories to enable | ['rhel-7-server-rpms', 'rhel-7-server-extras-rpms']  |

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Enable Red Hat repositories
  include_role:
    name: rhel_enable_repos
  vars:
    repos_to_enable:
      - rhel-7-server-rpms
      - rhel-7-server-extras-rpms
```

Note: add common variables to the `vars` list as required.
