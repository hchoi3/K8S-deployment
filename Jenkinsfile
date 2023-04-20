pipeline {
    // define the exact agent you want to use to run these jobs via label
    agent {
        label 'workernode1'
    }
    // Add an environment variable that contains the credentials for dockerhub defined in jenkins credentials settings
    environment {
        DOCKERHUB_CREDENTIALS=credentials('docker_registry')
    }

    stages {
        stage('Checkout') {
            steps {
                // Get some code from a GitHub repository
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Research-Associate-Internship/Hyunmin-Choi.git']]])
        
            }
        }  

        stage('Deploying App to Kubernetes') {
            steps {
                script {
                    kubernetesDeploy(configs: "deploymentservice.yml", kubeconfigId: "kubernetes")
                }   
      }
    }
}
}