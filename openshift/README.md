oc new-project redis
oc apply -f scc.yaml
oc adm policy add-scc-to-user redis-enterprise-scc system:serviceaccount:redis:rec
oc apply -f openshift.bundle.yaml
oc apply -f operator_rhel.yaml 


oc patch -n redis rec/rec --type=merge -p '{"metadata": {"finalizers":null}}'
oc delete po rec-0 --grace-period=0 --force
oc delete po rec-1 --grace-period=0 --force
oc delete po rec-2 --grace-period=0 --force
