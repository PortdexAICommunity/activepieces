pipeline {
    agent any

    environment {
        DEPLOYMENT_NAME = 'activepeices-portdes-ai'
        DEPLOYMENT_DOMAIN = 'activepieces.portdex.ai'
        // DEPLOYMENT_PORT = '80'  // Optional
    }

    stages {
        stage('Overriding') {
            steps {
                sh '''
                    export DEPLOYMENT_NAME=${DEPLOYMENT_NAME}
                    export DEPLOYMENT_DOMAIN=${DEPLOYMENT_DOMAIN}
                    export DEPLOYMENT_PORT=${DEPLOYMENT_PORT}

                    echo "- Overriding the docker-compose.yml file"
                    OVERRIDE
                    echo "- Overriding docker-compose.yml file completed"
                '''
            }
        }
        stage('Cleaning') {
            steps {
                sh '''
                    echo "- Cleaning the docker-compose.yml file"
                    docker compose -f docker-compose.override.yaml down
                    echo "- Cleaning docker-compose.yml file completed"
                '''
            }
        }
        stage('Building') {
            steps {
                sh '''
                    echo "- Building the docker-compose.yml file"
                    docker compose -f docker-compose.override.yaml pull
                    docker compose -f docker-compose.override.yaml build
                    echo "- Building docker-compose.yml file completed"
                '''
            }
        }
        stage('Deploying') {
            steps {
                sh '''
                    echo "- Deploying the docker-compose.yml file"
                    docker compose -f docker-compose.override.yaml up -d
                    echo "- Deploying docker-compose.yml file completed"
                '''
            }
        }
    }
}
