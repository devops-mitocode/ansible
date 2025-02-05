pipeline {
    agent {
        docker {
            image 'quay.io/ansible/ansible-runner:stable-2.12-latest'
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