pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://2350DBA74CEC5696A391F71DF9A03F01.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://2350DBA74CEC5696A391F71DF9A03F01.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
