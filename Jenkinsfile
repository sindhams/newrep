pipeline {
  
  agent { docker { image 'python:3.5.1' } }
  parameters {
    // Select the application or service you want updated. Even if you only have a single 
    // application or service now its good to plan for the future.
    string(name: 'devhyscaleclusters', defaultValue: 'dev-gke,dev-eks,dev-kops,dev-aks', description: 'Deploy this application or service')

    // Select the version you want deployed. This could be a semantic version or a 
    // git reference like a tag, branch, or SHA.
    string(name: 'blacklisted_ns', defaultValue: 'default,dev,devgrp1,devgrp2,ingress,monitoring,test,kube-node-lease,kube-public,kube-system,plhys', description: 'Deploy this version of the application or service')

    // Select the environment you want updated. Even if you only have a single 
    // environment now its good to plan for the future.
    //string(name: 'DEPLOY_ENV', default: 'dev', description: 'Deploy to this environment')
  }
  stages {
   stage('Deploy') {
     steps {
       // Ansible example
       // - Ansible should be preinstalled on the Jenkins servers
       // - need to store SSH key in Jenkins that can be used for deployments
       //withCredentials([sshUserPrivateKey(credentialsId: "deploy-ssh-key", keyFileVariable: 'deploy.pem')]) {
         sh """
         python --version
         python hw.py
         """
      }
    }
}
}
