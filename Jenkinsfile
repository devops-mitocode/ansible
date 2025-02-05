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

                    // sh 'ansible server1 -i hosts -m ping -u ec2-user'
                    // sh 'ansible server2 -i hosts -m ping -u ec2-user'
                    // sh 'ansible server1:server2 -i hosts -m ping -u ec2-user'
                    // sh 'ansible servers -i hosts -m ping -u ec2-user'
                    // sh 'ansible all -i hosts -m ping -u ec2-user'

                    // sh 'ansible server1 -i hosts -m command -a "cat /etc/os-release" -u ec2-user'
                    // sh 'ansible server1 -i hosts -a "cat /etc/os-release" -u ec2-user'
                    // sh 'ansible server1 -i hosts -m yum -a "name=wget state=latest" -u ec2-user --become'
                    // sh 'ansible server1 -i hosts -m ansible.builtin.yum -a "name=tree state=latest" -u ec2-user --become'

                    sh 'ansible-inventory -i hosts --list'
                    // sh 'ansible-inventory -i hosts --graph'
                    // sh 'ansible server1 -i hosts -m yum -a "name=git state=latest" -u ec2-user --become'


                    sh 'ansible-playbook -i hosts playbooks/server1_config.yml -u ec2-user --become'
                    sh 'ansible-playbook -i hosts playbooks/server1_jboss.yml -u ec2-user --become'
                }
            }
        }
    }
}