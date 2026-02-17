pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-shrikant', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://ec2-13-60-179-42.eu-north-1.compute.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-shrikant', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://ec2-13-60-179-42.eu-north-1.compute.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
