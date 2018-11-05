# ocp_ldap_sync

## Description:

Timed sync for ldap groups from AD

_Note: This role will only works with augmented AD schema

## Behaviour:

**Feature:** Builds custom image and creates cronjob object in Openshift to sync AD groups
**Given:** AD is available
**When:** After Openshift cluster is deployed

## Configuration:

Common variables used by this role:

| Variable  | Description  | Example  | 
|---|---|---|
| **ad_sync_bind_dn** | Bind DN | |
| **ad_sync_bind_password** | Bind password | |
| **ad_sync_group_search_dn** | Group search DN | |
| **ad_sync_ldap_url** | LDAP URL | |
| **ad_sync_user_search_dn** | User Search DN | |
| **ad_sync_schedule** | Cron schedule (default every 5 minutes)  | |

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Enable LDAP group sync
  include_role:
    name: oc_ldap_sync
  vars:
    ad_sync_bind_dn: cn=admin,dc=myorg,dc=net
    ad_sync_bind_password: my$secr3t_p4ssw0rd!!!
    ad_sync_group_search_dn: ou=groups,dc=myorg,dc=net
    ad_sync_user_search_dn: ou=users,dc=myorg,dc=net
    ad_sync_ldap_url: ldap://myadhost.myorg.net
    ad_sync_schedule: '*/5 * * * *'
```

Note: add common variables to the `vars` list as required.
