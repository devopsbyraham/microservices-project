pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-shekar', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://C4AF8509ACFFD9DEC6E3D9C6CB6684C6.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-shekar', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://C4AF8509ACFFD9DEC6E3D9C6CB6684C6.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
