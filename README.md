# selfservice-demo

oc create clusterrole namespace-patcher --verb=patch,create,update --resource=namespaces,limitranges,resourcequotas
oc adm policy add-cluster-role-to-user namespace-patcher system:serviceaccount:gpte-jenkins:jenkins
oc adm policy add-cluster-role-to-user self-provisioner system:serviceaccount:gpte-jenkins:jenkins

for i in $(oc get projects  | grep Terminating| awk '{print $1}'); do echo $i; oc get serviceinstance -n $i -o yaml | sed "/kubernetes-incubator/d"| oc apply -f - ; done
