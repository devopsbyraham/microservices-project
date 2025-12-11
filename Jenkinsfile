pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-rahamrrr', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://4AF1FCA2EF836606D3192716EF25E378.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-rahamrrr', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://4AF1FCA2EF836606D3192716EF25E378.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
