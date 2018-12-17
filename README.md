# selfservice-demo

oc create clusterrole namespace-patcher --verb=patch,create,update --resource=namespaces,limitranges,resourcequotas
oc adm policy add-cluster-role-to-user namespace-patcher system:serviceaccount:gpte-jenkins:jenkins
oc adm policy add-cluster-role-to-user self-provisioner system:serviceaccount:gpte-jenkins:jenkins
