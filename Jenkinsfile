pipeline {
    agent any

    tools {
        maven 'Maven_3'          // you already created this
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
        stage('Checkout') {
            steps {
                // Multibranch already checks out, but this is explicit
                echo "Code checked out for ${env.APP_NAME}"
            }
        }

        stage('Build') {
            steps {
                echo "Building ${env.APP_NAME}"
                // Example – safe command that always works:
                bat 'echo mvn clean install (placeholder)'
            }
        }

        stage('Static Code Analysis (SAST)') {
            steps {
                echo 'Running SAST scan (placeholder for SonarQube)'
                // In a real setup you would do something like:
                // bat 'sonar-scanner ...'
            }
        }

        stage('Dependency Check') {
            steps {
                echo 'Running dependency scan (placeholder for OWASP Dependency-Check)'
                // Example of where real command would go:
                // bat 'dependency-check ... --out reports\\dependency-check-report.html'
            }
        }

        stage('Container Image Scan') {
            steps {
                echo 'Running container scan (placeholder for Trivy/Anchore)'
                // bat 'trivy image myapp:latest'
            }
        }

        stage('Unit Tests') {
            when {
                expression { params.RUN_TESTS }   // link to your checkbox
            }
            steps {
                echo 'Running unit tests (placeholder for mvn test)'
                // bat 'mvn test'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying ${env.APP_NAME} to staging (${env.DEPLOY_ENV})"
                // bat 'echo kubectl apply -f k8s-deployment.yaml'
            }
        }

        stage('Security Gate') {
            steps {
                script {
                    // In a REAL pipeline you would parse a report file
                    // Here we just simulate that no High vulnerabilities were found
                    def hasHighVulns = false
                    if (hasHighVulns) {
                        error "Security vulnerabilities found. Aborting the pipeline!"
                    } else {
                        echo 'Security gate passed (no high vulnerabilities detected)'
                    }
                }
            }
        }

        stage('Deploy to Production') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying ${env.APP_NAME} to PRODUCTION"
                // bat 'echo kubectl apply -f k8s-prod-deployment.yaml'
            }
        }
    }

    post {
        always {
            echo 'Archiving security reports (placeholder)'
            // Example if you had reports:
            // archiveArtifacts artifacts: 'reports/**', allowEmptyArchive: true
        }
        success {
            echo '✅ Secure pipeline completed successfully!'
        }
        failure {
            echo '❌ Secure pipeline failed!'
        }
    }
}
