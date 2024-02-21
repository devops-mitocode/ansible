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
                
                sh 'cat /etc/os-release'

                sh 'whoami'

                sh 'ansible --version'

                sh 'cat /etc/ansible/hosts'


                sshagent (credentials: ['centos-private-key']) {
                    
                    sh 'ansible server1 -i hosts -a "cat /etc/os-release" -u ec2-user'

                    sh 'ansible server1 -i hosts -m yum -a "name=wget state=latest" -u ec2-user --become'

                    sh 'ansible server1 -i hosts -m yum -a "name=nmap state=latest" -u ec2-user --become'

                    sh 'ansible server1 -i hosts -m yum -a "name=java-17-openjdk state=latest" -u ec2-user --become'

                    sh 'ansible-playbook -i hosts playbook/playbook.yml'
                }
            }
        }
    }
}