pipeline {
    agent any

    stages {
        stage('Deploy to K8') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'Microservice-token', namespace: 'webapps', serverUrl: 'https://D38A51CA0CEC7CFBB816A962679E3E24.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'Microservice-token', namespace: 'webapps', serverUrl: 'https://D38A51CA0CEC7CFBB816A962679E3E24.gr7.us-east-1.eks.amazonaws.com']]) {
                   sh "kubectl get all -n webapps "
               }
            }
        }
        
       
    }
}
