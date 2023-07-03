
###
https://developer.hashicorp.com/vault/docs/platform/k8s/helm/openshift

```

helm install vault hashicorp/vault  --values  values.openshift.yaml

vault operator init

vault operator unseal
vault operator unseal
vault operator unseal

wget  https://github.com/RedisLabs/vault-plugin-database-redis-enterprise/releases/download/v0.1.3/vault-plugin-database-redis-enterprise_0.1.3_linux_amd64  -O  /usr/local/libexec/vault/vault-plugin-database-redisenterprise_linux_amd64 

export VAULT_TOKEN=...
vault write sys/plugins/catalog/database/redisenterprise-database-plugin command=vault-plugin-database-redisenterprise_linux_amd64 sha256=739421599adfe3cdc53c8d6431a3066bfc0062121ba8c9c68e49119ab62a5759
vault secrets enable database


vault write database/config/redis-rec-mydb plugin_name="redisenterprise-database-plugin" url="https://rec.redis.svc.cluster.local:9443" allowed_roles="*" database=mydb username=demo@redis.com password=PVcYQE6F
vault write database/roles/mydb db_name=redis-rec-mydb creation_statements="{\"role\":\"DB Member\"}" default_ttl=3m max_ttl=10m

## get in the vault pod

vault token create 

## create the Route to vault service and port 8200 and log in the UI with token


## enable database
vault secrets enable database


## get the cluster admin cred
kubectl -n redis get secret/rec -o=jsonpath={.data.username} | base64 -d
kubectl -n redis get secret/rec -o=jsonpath={.data.password} | base64 -d

vault write database/config/redis-test-mydb plugin_name="redisenterprise-database-plugin" url="https://rec.redis.svc.cluster.local:9443" allowed_roles="*" database=mydb username=demo@redis.com password=PVcYQE6F

```
