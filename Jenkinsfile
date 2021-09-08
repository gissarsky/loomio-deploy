pipeline {
    agent { label "agent1" }
    
    stages {
        stage("Create env") {
            steps {
                sh '''
                chmod +x ./scripts/create_env
                ./scripts/create_env loomio.example.com you@contact.email
                '''                
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