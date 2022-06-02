pipeline {
    agent any

    stages {
        stage('Build and package app') {
            steps {
                ansiblePlaybook(
                playbook: 'mvn.yml'
                )
            }
        }
        stage('Generate AWS keypair') {
            steps {
                ansiblePlaybook(
                    playbook: 'ec2_newKeypair.yml'
                    
                )
            }     
        }
        stage('Launch EC2 Instance') {
            steps {
                ansiblePlaybook(
                   playbook: 'create_host.yml'
                                       
                )
            }
        }
        stage('Provision Tomcat') {
            steps {
                ansiblePlaybook(
                    playbook: 'tomcat.yml',
                    inventory: 'hosts.ini'
                )
            }
        }
        stage('Deploy App') {
            steps {
                ansiblePlaybook(
                    playbook: 'copy_webapp.yml',
                    inventory: 'hosts.ini'
                )
            }
        }
    }
}
