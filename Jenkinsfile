pipeline {
    agent any

    stages {
        stage('Deploy to k8s') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9F52DB7EAA087D54BE085F0C0E05D789.gr7.ap-south-1.eks.amazonaws.com']]) {
                       sh "kubectl apply -f deployment-service.yml"
                       sleep 60
                 }
            }
        }
        
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9F52DB7EAA087D54BE085F0C0E05D789.gr7.ap-south-1.eks.amazonaws.com']]) {
                         sh "kubectl get svc -n webapps"
                   }
            }
        }
    }
}

