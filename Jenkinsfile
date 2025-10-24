pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5490ACBD07793EEFC597350EF61090F6.gr7.us-west-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5490ACBD07793EEFC597350EF61090F6.gr7.us-west-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
