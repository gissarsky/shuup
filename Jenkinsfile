pipeline {
    agent { label "agent1" }
    stages {
        stage("build app") {
            steps {
                script {
                    echo "building the app.." 
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    echo "building the shuup docker image.."
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PSW', usernameVariable: 'USER')]) {
                        sh 'docker build -t exadeldevops/shuup:1.0 .'
                        sh "docker login -u $USER -p $PSW"
                        sh 'docker push exadeldevops/shuup:1.0'
                    }    
                }
            }
        }
        stage("deployment") {
            environment {
                AWS_ACCESS_KEY_ID = credentials('jenkins_aws_access_key_id')
                AWS_SECRET_ACCESS_KEY = credentials('jenkins_aws_secret_access_key')
                APP_NAME = 'shuup-app'
            }
            steps {
                sh 'envsubst < kubernetes/deployment.yaml | kubectl apply -f -'
                sh 'envsubst < kubernetes/service.yaml | kubectl apply -f -'                 
            }
        }
    }
}
