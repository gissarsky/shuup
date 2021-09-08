pipeline {
    agent { label "agent1" }
    stages {
        stage("Deploy") {
            steps {
                sh '''
                    docker-compose up                    
                    '''         
            }
        }
    }
} 