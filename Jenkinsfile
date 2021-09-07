pipeline {
    agent { label "agent1" }
    stages {
        stage("Deploy") {
            steps {
                sh '''
                    docker-compose -f docker-compose-dev.yml up
                    docker-compose ps --format json
                    '''         
            }
        }
    }
} 