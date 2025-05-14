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
    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }
    stages {
        stage('ansible') {
            steps {
                sh 'ansible --version'
                sh 'whoami'
                sh 'env | sort'

                sshagent (credentials: ['amazon-linux-private-key']) {
                    sh 'ansible server1 -i hosts -m ping -u ec2-user'
                    // sh 'ansible server1:server3 -i hosts -m ping -u ec2-user'
                    // sh 'ansible servers -i hosts -m ping -u ec2-user'
                    // sh 'ansible all -i hosts -m ping -u ec2-user'

                    sh 'ansible server1 -i hosts -a "cat /etc/os-release" -u ec2-user'

                }
            }
        }
    }   
}
