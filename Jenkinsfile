pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://9FED4B0396D1AFD66614FA503B9B4833.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://9FED4B0396D1AFD66614FA503B9B4833.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
