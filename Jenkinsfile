pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-shrikant', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://38F56F62715485EEEBCD2B68441AF62F.sk1.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-shrikant', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://38F56F62715485EEEBCD2B68441AF62F.sk1.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
