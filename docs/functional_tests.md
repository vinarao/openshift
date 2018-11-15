# OCP Functional Tests

## HC - Cluster Health Checks

| Ref |Check  | Description | Commands | 
|---|---|---|---|
| HC01 | All nodes available| Check that nodes are running and available. | $ oc get nodes |
| HC02 | Internal registry running | Check that the internal registry is running. | $ oc get pods |
| HC03 | App routers are running | Check the application routers pods are running. | $ oc get pods |
| HC04 | General diagnostics | Check the basic services are operating correctly. | $ oc adm diagnostics |
| HC05 | Role binding consistency. | Check the role bindings are consistent with base policy. | $ oc adm diagnostics clusterrolebindings |

