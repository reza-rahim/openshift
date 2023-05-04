kubectl config set-context --current --namespace=redis
oc apply -f scc.yaml 
oc adm policy add-scc-to-user redis-enterprise-scc system:serviceaccount:redis:redis-enterprise-operator
oc adm policy add-scc-to-user redis-enterprise-scc system:serviceaccount:redis:rec

