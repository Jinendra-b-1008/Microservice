pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8A5E09BA762ECB3E1C344CF248DCC3F2.yl4.ap-south-1.eks.amazonaws.com']]) {
                
                    sh '''kubectl apply -f deployment-service.yml
                    
                    sleep 60
                    '''
                    
                     
                }
            }
        }
          stage('Verify deplyment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8A5E09BA762ECB3E1C344CF248DCC3F2.yl4.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl get svc -n webapps"
                     
                }
            }
        }
    }
}
