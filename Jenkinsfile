pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment { 
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') { 1
            steps {
                sh './jenkins/scripts/deliver.sh' 2
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 3
                sh './jenkins/scripts/kill.sh' 4
            }
        }
    }
}
