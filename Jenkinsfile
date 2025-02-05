pipeline {
    agent {
        docker {
            image 'alpine/ansible:2.18.1'
            // image 'quay.io/ansible/ansible-runner:stable-2.12-latest'
            args '-u root'
        }
    }
    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }
    stages {
        stage('ansible') {
            steps {
                sh 'ansible --version'
                sh 'whoami'

                sshagent (credentials: ['centos-private-key']) {

                    sh 'ansible server1 -i hosts -a "cat /etc/os-release" -u ec2-user'
                }
            }
        }
    }
}