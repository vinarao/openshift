# GlusterFS 

## Two Data Centre Topology

In the case where only two data centres are available for deployment; or when there are three data centres but the network 
link with the third one has relatively high latency creating data synchronisation issues for GlusterFS, the proposed
GlusterFS topology is as described below.

Each data centre will contain two GlusterFS nodes configured to use replica-3 distributed replicated volumes.

In the event of a data centre failure where only two (out of four) GlusterFS nodes remain active, the nodes will go into Read-Only mode.

This is due to the fact that the cluster needs more than 50% of the nodes to be able to perform write operations.
This prevents split brain scenarios; that is, data inconsistencies as a result of a separate sets of nodes writing to 
the same data source.

In the event of a data centre failure where there are two pair of two isolated GlusterFS nodes, each set will still go 
into Read-Only mode separately, preventing split brain scenarios.

The four-node replica-3 configuration ensures that there is at least one replica in each data centre (i.e. two
replicas in one and one replica in the other) but at the same time there is a highly available (read-only) set in case 
of a data centre failure. 

OpenShift applications requiring to write data will fail as soon as GlusterFS goes into read only mode.
This is typically the case of logging and metrics. The docker registry will continue operating for image pull but 
deployment of applications will fail as they try and write images into the registry.

Where applications use databases external to OpenShift, they will continue operating with failure in logging and metrics.

In order to put the GlusterFS back into read-write mode, it is necessary to add a third node into the data centre where 
the two remaining GlusterFS nodes are located.

This can be done in the following ways, with different Recovery Time Objective (RTO):

- **Cold Standby**: A new GlusterFS is provisioned from the ground up. This entails the spinning of a new RHEL node, the hardening and 
deployment of the GlusterFS software. With the deployment process fully automated, the RTO depends on the provisioning 
time for RHEL nodes in the underlying platform. Assuming a provisioning time of 1 hour or less, the RTO could be within 2 hours.

- **Warm Standby**: An GlusterFS node is already available and ready to be joined in the GlusterFS cluster.
With the addition of the node to the cluster is fully automated, the RTO could be within 30 minutes.

