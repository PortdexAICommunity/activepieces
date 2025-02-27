pipeline {
    agent any

    environment {
        DEPLOYMENT_NAME = 'activepieces-portdexai'
        DEPLOYMENT_DOMAIN = 'activepieces.portdex.ai'
        // DEPLOYMENT_PORT = '80'  // Optional
    }

    stages {
        stage('Deployment') {
            steps {
                sh '''
                    export DEPLOYMENT_NAME=${DEPLOYMENT_NAME}
                    export DEPLOYMENT_DOMAIN=${DEPLOYMENT_DOMAIN}
                    # export DEPLOYMENT_PORT=${DEPLOYMENT_PORT}

                    DEPLOYMENT
                '''
            }
        }
    }
}
