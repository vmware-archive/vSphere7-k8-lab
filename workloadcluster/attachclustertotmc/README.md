# Attach Cluster to TMC
Login as admin:

```bash
vsphere login --insecure-skip-tls-verify --managed-cluster-name=application-catalog --server wcp.haas-435.pez.pivotal.io -u alana@vsphere.local

kubectl config use-context wordpress

export ID=YOURID
export TMC_CLUSTER_GROUP=your_cluster_group
export TMC_CLUSTER= wordpress

tmc login --name $ID --no-configure
tmc cluster attach\
  --name $TMC_CLUSTER\
  --labels origin=$ID\
  --group $TMC_CLUSTER_GROUP\
  --output workloadcluster/attachclustertotmc/tmc-wordpress-cluster-attach.yaml
kubectl apply -f workloadcluster/attachclustertotmc/tmc-wordpress-cluster.yaml
```