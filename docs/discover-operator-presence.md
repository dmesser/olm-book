# How do I discover the presence/availability of an Operator?

## Discovering installed operators
Checking the presence of custom installed operators in the cluster is simply a matter of checking all the 
`ClusterServiceVersions` (CSV) that are available in the cluster. Every  operator installed by OLM has a corresponding CSV
associated with it that that contains all the details of the operator. Running `kubectl get csvs -A`
would return all CSVs across all namespaces and provide a high-level view of all custom installed operators. 

If the ClusterServiceVersion fails to show up or does not reach the `Succeeded` phase, please check the [troubleshooting documentation](https://) to debug your installation.  

## Finding available operators
Operators are available from a variety of sources. The most straightforward option is to use the OperatorHub, an online catalog
of available operators available on an OpenShift cluster. OpenShift documentation provides a [step by step guide](https://docs.openshift.com/container-platform/4.2/operators/olm-adding-operators-to-cluster.html#olm-installing-from-operatorhub-using-web-console_olm-adding-operators-to-a-cluster)
on installing operators via OperatorHub. This is the recommended way of finding and installing operators to a cluster.

Another option is to install operators manually via the command line. This is more involved and manual but provides a high degree
of flexibility around operator installation. OpenShift documentation also provides a [step by step](https://docs.openshift.com/container-platform/4.2/operators/olm-adding-operators-to-cluster.html#olm-installing-operator-from-operatorhub-using-cli_olm-adding-operators-to-a-cluster)
guide on installing operators from the CLI.

To get more information about a particular operator installed within the cluster from a catalogsource, run 
`kubectl describe packagemanifests <operator name>`. This will provide some detailed information about the operator such as 
its intended use, applicable CRDs, and resources for support with that particular operator. 