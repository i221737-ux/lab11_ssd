pipeline {
    agent any

    tools {
        maven 'Maven_3'     // same name as in Global Tool Configuration
    }

    parameters {
        booleanParam(
            name: 'RUN_TESTS',
            defaultValue: true,
            description: 'Run the Test stage?'
        )
    }

    environment {
        APP_NAME   = 'lab11_ssd'
        DEPLOY_ENV = 'dev'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building ${env.APP_NAME}"
                bat 'mvn -version'
            }
        }

        stage('Test') {
            when {
                expression { params.RUN_TESTS }
            }
            steps {
                echo "Running tests for ${env.APP_NAME}"
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
