pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://E2C4F5FC0EF825F21286DECF16C2D5BF.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://E2C4F5FC0EF825F21286DECF16C2D5BF.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
