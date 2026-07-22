pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-k8s', contextName: '', credentialsId: 'kubernetes-cred', namespace: 'webapps', serverUrl: 'https://8B67551F113C3C4E79E720C9D3A1A55C.gr7.ap-south-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-k8s', contextName: '', credentialsId: 'kubernetes-cred', namespace: 'webapps', serverUrl: 'https://8B67551F113C3C4E79E720C9D3A1A55C.gr7.ap-south-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
