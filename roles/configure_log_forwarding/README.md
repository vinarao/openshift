# ocp_external_logging

## Description:

Configures platform logs to be sent to external Elasticsearch.

_Note: Needs to be extended to distribute client certificates

## Behaviour:

**Feature:** Reconfigures fluentd's daemonset to send 'ops' logs elswhere
**Given:** Hosted metrics are deployed
**Given:** External elastic search is deployed and reachable from cluster nodes
**When:** After Openshift hosted metrics are deployed

## Configuration:

Common variables used by this role:

| Variable  | Description  | Example  | 
|---|---|---|
| **amos_logging_fluentd_scheme** | Is external elasticsearch http or https | |
| **amos_ops_host** | Address of external Elasticsearch | |
| **amos_ops_port** | Port of external Elasticsearch | |
| **amos_logging_fluentd_ops_client_cert** | Certificate for client authenthication (container path) | |
| **amos_logging_fluentd_ops_client_key** | Key for client authenthication (container path) | |
| **amos_logging_fluentd_ops_ca** | CA for client authenthication (container path) | |


## Usage:

How to invoke the role from a playbook:

```yaml
- name: Configure external logging
  include_role:
    name: ocp_external_logging
  vars:
    amos_ops_host: myelasticsearch.net
```

Note: add common variables to the `vars` list as required.
