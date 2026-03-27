pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 gunduabhinaya29/paytm:bank'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerid') {
                        sh 'docker push gunduabhinaya29/paytm:bank'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 gunduabhinaya29/paytm:bank'
            }
        }
    }
}
