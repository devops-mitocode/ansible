pipeline {
    agent {
        docker {
            image 'alpine/ansible:2.18.1'
            args '-u root'
        }
    }
    options {
        ansiColor('xterm')
    }
    stages {
        stage('ansible') {
            steps {
                sh 'ansible --version'
            }
        }
    }   
}
