# rhel_packages

## Description:

Install required packages

## Behaviour:

**Feature:** Install list of packages

## Configuration:

Common variables used by this role:

| Variable  | Description  | Example  | 
|---|---|---|
| **packages_to_install** | List of Red Hat packages to install | |

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Install Red Hat packages
  include_role:
    name: rhel_packages
  vars:
    repos_to_enable:
      - httpd
      - vim
```

Note: add common variables to the `vars` list as required.
