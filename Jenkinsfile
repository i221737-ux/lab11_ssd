pipeline {
    agent any

    tools {
        maven 'Maven_3'      // same name as in Jenkins tool config
    }

    environment {
        APP_NAME = 'lab11_ssd'
        DEPLOY_ENV = 'dev'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building ${env.APP_NAME}"
                bat 'mvn -version'     // just to show Maven is available
            }
        }

        stage('Test') {
            steps {
                echo "Testing ${env.APP_NAME}"
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying ${env.APP_NAME} to ${env.DEPLOY_ENV}"
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline finished successfully'
        }
        failure {
            echo '❌ Pipeline failed'
        }
        always {
            echo 'ℹ️ Post section executed (always)'
        }
    }
}
