pipeline {
    agent { label "agent1" }
    stages {
        stage("Deploy") {
            steps {
                sh '''
                    sudo docker-compose up
                    sudo docker-compose ps --format json
                    '''         
            }
        }
    }
} 