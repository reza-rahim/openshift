
###
https://developer.hashicorp.com/vault/docs/platform/k8s/helm/openshift

```

helm install vault hashicorp/vault     --set "global.openshift=true"     --set "server.dev.enabled=true"

```
