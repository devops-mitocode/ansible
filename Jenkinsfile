pipeline {
    agent {
        docker {
            image 'quay.io/ansible/ansible-runner:stable-2.12-latest'
            args '-u root'
        }
    }
    stages {
        stage('ansible') {
            steps {
                sh 'ansible --version'

                sh 'ansible server1 -i hosts -a "cat /etc/os-release" -u ec2-user'
            }
        }
    }
}