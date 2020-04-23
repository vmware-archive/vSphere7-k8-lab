# Deploy WaveFront

Login to Pivotal Okta to get API_KEY from wavefront

```bash
export API_KEY=API_KEY
export VMWARE_ID=YOUR_VMWARE_ID

kubectl create namespace wavefront
helm install wavefront wavefront/wavefront \
  --set wavefront.url=https://surf.wavefront.com \
  --set wavefront.token=$API_KEY \
  --set clusterName=$VMWARE_ID-svc-cluster \
  --namespace wavefront
```

## Access wavefront

https://surf.wavefront.com and filter the cluster list to your $VMWARE_ID-svc-cluster.