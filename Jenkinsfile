pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://53A0BE9FC315B5C508ECFBFD36D9A180.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://53A0BE9FC315B5C508ECFBFD36D9A180.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
