pipeline {
    agent { label "agent1" }
    stages {
        stage("Deploy") {
            steps {
                sh '''
                    docker compose up
                    docker compose ps --format json
                    '''         
            }
        }
    }
} 