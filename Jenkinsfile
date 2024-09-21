pipeline {
    agent {
        docker {
            image 'quay.io/ansible/ansible-runner:stable-2.12-latest'
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

                sshagent(credentials: ['centos-private-key']) {
                    sh 'ansible server1 -i hosts -m command -a "cat /etc/os-release" -u ec2-user'
                    sh 'ansible server1 -i hosts -m ping -u ec2-user'

                    sh 'ansible server2 -i hosts -m ping -u ec2-user'
                }
            }
        }           
    }
}