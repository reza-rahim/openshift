oc new-project redis
oc apply -f scc.yaml
oc adm policy add-scc-to-user redis-enterprise-scc system:serviceaccount:redis:rec
oc apply -f openshift.bundle.yaml


oc patch -n redis rec/rec --type=merge -p '{"metadata": {"finalizers":null}}'
