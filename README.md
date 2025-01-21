# openshift

##### link
  - https://two-oes.medium.com/openshift-4-in-an-air-gap-disconnected-environment-part-1-prerequisites-63f065e8a729


##### How to get install for ocp version

  - https://console.redhat.com/openshift/install/gcp/user-provisioned
  - https://mirror.openshift.com/pub/openshift-v4/clients/ocp/

####
  - https://access.redhat.com/documentation/en-us/openshift_container_platform/

```
export GOOGLE_APPLICATION_CREDENTIALS=/root/redislabs-sa-training-services-039940d51d47.json

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


export KUBECONFIG=


oc patch -n redis rec/rec --type=merge -p '{"metadata": {"finalizers":null}}'

oc adm node-logs  demo-3-btnlq-worker-a-658m7 -u kubelet 

oc delete po rec-0 --grace-period=0 --force  

```
