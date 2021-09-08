pipeline {
    agent { label "agent1" }
    stages {
        stage("Setup a swapfile") {
            steps {
                sh "./scripts/create_swapfile"         
            }
        }
        stage("Initialize the database") {
            steps {
                sh '''
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