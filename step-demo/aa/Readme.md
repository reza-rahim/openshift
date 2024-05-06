# cluster 1
export KUBECONFIG=/root/demo-1/auth/kubeconfig 
oc new-project ns1
oc apply -n ns1 -f openshift.bundle.yaml
oc apply -n ns1 -f scc.yaml
oc adm policy add-scc-to-user redis-enterprise-scc  system:serviceaccount:ns1:rec01

 oc apply -n ns1 -f  rec01_rhel.yaml 

oc apply -n ns1 -f rerc_crd.yaml
oc apply -n ns1 -f reaadb_crd.yaml 
oc patch cm  operator-environment-config --type merge --patch "{\"data\": \
{\"ACTIVE_ACTIVE_DATABASE_CONTROLLER_ENABLED\":\"true\", \
\"REMOTE_CLUSTER_CONTROLLER_ENABLED\":\"true\"}}"


# cluster 2
export KUBECONFIG=/root/demo-2/auth/kubeconfig 
oc new-project ns2
oc apply -n ns2 -f openshift.bundle.yaml
oc apply -n ns2 -f scc.yaml
oc adm policy add-scc-to-user redis-enterprise-scc  system:serviceaccount:ns2:rec02

oc apply -n ns2 -f  rec02_rhel.yaml 


oc apply -n ns2 -f rerc_crd.yaml
oc apply -n ns2 -f reaadb_crd.yaml 
oc patch cm  operator-environment-config --type merge --patch "{\"data\": \
{\"ACTIVE_ACTIVE_DATABASE_CONTROLLER_ENABLED\":\"true\", \
\"REMOTE_CLUSTER_CONTROLLER_ENABLED\":\"true\"}}"


## on the cluster 2
## setting up the  secret

oc apply -n ns2 -f all-rec-secrest.yaml 
oc apply -n ns2 -f rerc1-file.yaml 
oc apply -n ns2 -f rerc2-file.yaml 
oc get rerc  rerc1
oc get rerc  rerc2

