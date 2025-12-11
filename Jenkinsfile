pipeline {
    agent {
        docker {
            image 'alpine/ansible:2.18.6'
            // args '-u root'
        }
    }
    stages {
        stage('ansible') {
            steps {
                sh 'whoami'
                sh 'ansible --version'
            }
        }
    }
}