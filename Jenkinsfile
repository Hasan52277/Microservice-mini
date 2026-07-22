pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E0324E8D4156D81C1AAFBEE9A8955820.yl4.ap-south-1.eks.amazonaws.com']]) {
                 sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
         stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E0324E8D4156D81C1AAFBEE9A8955820.yl4.ap-south-1.eks.amazonaws.com']]) {
               sh "kubectl get svc -n webapps"
               }
            }
        }
    }
}
