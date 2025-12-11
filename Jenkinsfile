pipeline {
    agent {
        docker {
            image 'alpine/ansible:2.18.6'
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