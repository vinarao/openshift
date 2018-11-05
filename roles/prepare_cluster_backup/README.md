# ocp_backup

## Description:

Creates local OCP configuration backup

## Behaviour:

**Feature:** Copies important OCP config directories localy and archives them. On etcd nodes takes etcd snapshot and adds to local backup.
**Expected:** Calling playbook should copy local archive somewhere remotelly
**When:** Openshift cluster is deployed

## Configuration:

Common variables used by this role:

| Variable  | Description  | Example  | 
|---|---|---|
| **ocp_remote_backup_dir** | Local directory to hold a backup | |
| **ocp_directories_to_backup** | List of directories to backup across the cluster | |
| **ocp_etcd_directories_to_backup** | List of directories to backup on etcd nodes | |

ocp_etcd_directories_to_backup:

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Create local backups
  roles:
    - ocp_backup
```
