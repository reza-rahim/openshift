# openshift

##### link
  - https://two-oes.medium.com/openshift-4-in-an-air-gap-disconnected-environment-part-1-prerequisites-63f065e8a729


##### How to get install for ocp version
  - https://mirror.openshift.com/pub/openshift-v4/clients/ocp/

####
  - https://access.redhat.com/documentation/en-us/openshift_container_platform/

```
./openshift-install create install-config --dir demo-3
cp install-config.yaml dem0-3/
./openshift-install create cluster --dir demo-3

#UI
https://console-openshift-console.apps.demo-3.ps-redis.com/k8s/ns/redis/core~v1~Pod
## get the password for
cat demo-3/auth/kubeadmin-password

oc new-project redis
oc apply -f config/scc.yaml
oc adm policy add-scc-to-user redis-enterprise-scc system:serviceaccount:redis:rec
```
