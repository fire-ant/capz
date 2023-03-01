### CAPI CLUSTER-API-PROVIDER-AZURE Infrastructure Provider Chart

This chart is derived from the cluster-api-provider-azure infrastructure provider of the [Cluster API](https://cluster-api.sigs.k8s.io) project 

see https://github.com/kubernetes-sigs/cluster-api-provider-azure

### Values
for Chart Values see [here](charts/capz/README.md)

#### Notes

Note that Chart releases correlate image versions with CRDs and as such may need to upgrade/replace CRD versions over time.
the cluster-api-provider-azure project requires a bootstrap secret/credential which is hardcoded to:
```
apiVersion: v1
data:
  client-id: <AZURE_CLIENT_ID_B64>
  client-secret: <AZURE_CLIENT_SECRET_B64>
  subscription-id: <AZURE_SUBSCRIPTION_ID_B64>
  tenant-id: <AZURE_TENANT_ID_B64>
kind: Secret
metadata:
  labels:
    cluster.x-k8s.io/provider: infrastructure-azure
  name: capz-manager-bootstrap-credentials
  namespace: capz-system
type: Opaque
```
The credentials will need to be generated separately and managed outside of the chart.
