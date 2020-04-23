# Attach Cluster to TMC
Login as admin:

```bash
vsphere login --insecure-skip-tls-verify --managed-cluster-name=application-catalog --server wcp.haas-435.pez.pivotal.io -u alana@vsphere.local

kubectl config use-context application-catalog
export ID=YOURID
export TMC_CLUSTER_GROUP=your_cluster_group
export TMC_CLUSTER=application-catalog
tmc login --name $ID --no-configure
tmc cluster attach\
  --name $TMC_CLUSTER\
  --labels origin=$ID\
  --group $TMC_CLUSTER_GROUP\
  --output servicecluster/attachclustertotmc/tmc-svc-cluster-attach.yaml
kubectl apply -f servicecluster/attachclustertotmc/tmc-svc-cluster-attach.yaml
```