node {
	stage("Create Workspace") {
	    echo "Creating Projects"
        sh "oc new-project ${uid}-workspace"
    }
    stage("Assign Role") {
	    echo "Assign admin to project"
        sh "oc adm policy add-role-to-user admin  ${uid} -n ${uid}-workspace"
    }
	stage("Set Quota") {
	    echo "Setting quota for the project"
        sh "oc create quota projectquota --hard=limits.memory=2Gi,limits.cpu=1 -n ${uid}-workspace"
    }
    //stage("Set Limits") {
    //	LIMITSSET = '{\\"apiVersion\\":\\"v1\\",\\"kind\\":\\"LimitRange\\",\\"metadata\\":{\\"name\\":\\"resource-limits\\",\\"namespace\\":\\"tommy-workspace\\",},\\"spec\\":{\\"limits\\":[{\\"max\\":{\\"cpu\\":\\"200m\\",\\"memory\\":\\"250Mi\\"},\\"min\\":{\\"cpu\\":\\"100m\\",\\"memory\\":\\"100Mi\\"},\\"type\\":\\"Pod\\"}]}}' 
	//	sh "echo ${LIMITSSET} > limits.json "
	//	sh "oc create -f limits.json -n ${uid}-workspace"
    //}
}

node {
	stage("Remove Workspace") {
	    echo "Deleting Projects"
        sh "oc delete project ${uid}-workspace"
    }
}
