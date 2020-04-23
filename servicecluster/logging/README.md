# Fluent bit

## Deploy fluent-bit

Login as admin

```bash
kubectl vsphere login --insecure-skip-tls-verify --managed-cluster-name=application-catalog --server wcp.haas-435.pez.pivotal.io -u alana@vsphere.local
```


```bash
kubectl apply -f tkg-extensions/logging/fluent-bit/vsphere/00-fluent-bit-namespace.yaml
kubectl apply -f tkg-extensions/logging/fluent-bit/vsphere/01-fluent-bit-service-account.yaml
kubectl apply -f tkg-extensions/logging/fluent-bit/vsphere/02-fluent-bit-role.yaml
kubectl apply -f tkg-extensions/logging/fluent-bit/vsphere/03-fluent-bit-role-binding.yaml
# Change following parameters in 04-fluent-bit-configmap.yaml

<TKG_CLUSTER_NAME> to the name of the tkg cluster.

<TKG_INSTANCE_NAME> to the name of tkg instance. This name should be the same for management cluster and all the workload clusters that form a part of one TKG deployment.

<FLUENT_ELASTICSEARCH_HOST> to service name of Elasticsearch within your cluster.

<FLUENT_ELASTICSEARCH_PORT> to the appropriate port Elastic Search server is listening to.

kubectl apply -f tkg-extensions/logging/fluent-bit/vsphere/output/elasticsearch/04-fluent-bit-configmap.yaml
kubectl apply -f tkg-extensions/logging/fluent-bit/vsphere/output/elasticsearch/05-fluent-bit-ds.yaml
```
All fluent bit pods should be running

```bash
kubectl get po -n tanzu-system-logging
```
