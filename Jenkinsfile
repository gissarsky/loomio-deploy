pipeline {
    agent { label "agent1" }
    stages {
        stage("Initialize the database") {
            steps {
                sudo sh '''
                docker-compose up -d db
                docker-compose run app rake db:setup
                '''                
            }
        }
        stage("Starting the services") {
            steps {
                sh "docker-compose up -d"                
            }
        }
    }
}