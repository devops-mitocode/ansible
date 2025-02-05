pipeline {
    agent {
        docker {
            image 'alpine/ansible:2.18.1'
            // image 'quay.io/ansible/ansible-runner:stable-2.12-latest'
            args '-u root'
        }
    }
    stages {
        stage('ansible') {
            steps {
                sh 'ansible --version'
            }
        }
    }
}