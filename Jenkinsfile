pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Test-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5EF3D154C4810ACCB79108AF79A2B453.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Test-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5EF3D154C4810ACCB79108AF79A2B453.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
