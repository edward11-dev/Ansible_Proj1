pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh """
                echo 'Building..'
                docker build -t profed11/devops_proj2:latest .
                docker login -u "profed11" -p "eR-PaE9Evrun7!Z" docker.io
                docker push profed11/devops_proj2:latest
                """
            }
        }
        stage('Creating Docker Container') {
            steps {
                sh """
                echo 'Creating Docker Container...'
                pip install docker-compose
                chmod +x /var/lib/jenkins/.local/bin/docker-compose
                /var/lib/jenkins/.local/bin/docker-compose up -d --remove-orphans
                docker ps -a
               """
            }     
        }
    }
}
