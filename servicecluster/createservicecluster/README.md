# Create Service Cluster

Login as admin.

```bash
kubectl vsphere login --insecure-skip-tls-verify --server your-wcp-server -u administrator@vsphere.local
```

Username: administrator@vsphere.local
PW: VMware1!

Switch to the namespace we created.
```
kubectl config use-context <namespace>
```

Make sure to use the correct Storage Class that you created and Namespace in the manifest file.

![](../.././images/workloadcluster1.png)

```bash
kubectl apply -f scripts/create-service-cluster.yaml
```

SOMETIMES THE GUEST CLUSTER DOES NOT SHOW UP IN THE VSPHERE UI. 
YOU MAY HAVE TO DELETE AND DO IT AGAIN.

```
kubectl config use-context application-catalog
```