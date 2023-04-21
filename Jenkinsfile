pipeline {
    // define the exact agent you want to use to run these jobs via label
    agent {
        label 'workernode1'
    }

    stages {
        stage('Checkout') {
            steps {
                // Get some code from a GitHub repository
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/hchoi3/K8S-deployment.git']]])
        
            }
        }  

        stage('Deploying App to Kubernetes') {
            steps {
                script {
                    withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'k8s', namespace: '', restrictKubeConfigAccess: false, serverUrl: '') {
                        sh "kubectl apply -f deploymentservice.yml"        
                    }
                }   
      }
    }
}
}