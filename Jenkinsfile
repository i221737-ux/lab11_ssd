pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'      // Deploy only when branch is 'main'
            }
            steps {
                echo 'Deploying....'
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
