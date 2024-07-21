pipeline {
    agent any
    stages {
        stage('Update Dependencies') {
            steps {
                sh 'npm install -g npm@latest'  // Update npm to the latest version
                sh 'npm outdated'               // List outdated packages
                sh 'npm update'                 // Update packages to the latest version
            }
        }
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
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
