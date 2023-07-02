
###
https://developer.hashicorp.com/vault/docs/platform/k8s/helm/openshift

```

helm install vault hashicorp/vault     --set "global.openshift=true"     --set "server.dev.enabled=true"

## get in the vault pod

vault token create 

## create the Route to vault service and port 8200 and log in the UI with token

```
