pipeline {
    agent { label "agent1" }
    stages {
        stage("Setup a swapfile") {
            steps {
                sh '''
                    ./scripts/create_swapfile
                    '''        
                    }

            steps {
                sh '''
                    docker-compose up -d db
                    docker-compose run app rake db:setup
                    '''         
                    }

            steps {
                sh '''
                    docker-compose up -d
                    
                    '''         
                    }
                
            
        }
    } 
}    