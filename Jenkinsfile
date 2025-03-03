pipeline {
    agent any

    triggers {
        cron('H/3 * * * 1')  // Trigger every 3 minutes on Mondays
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Build the project (e.g., using Maven)
                    sh './mvnw clean install'
                }
            }
        }

        stage('Jacoco Code Coverage') {
            steps {
                script {
                    // Run tests and generate Jacoco code coverage report
                    sh './mvnw clean test jacoco:report'
                }
            }
        }

        stage('Generate Artifact') {
            steps {
                script {
                    // Package the application into an artifact (e.g., JAR)
                    sh './mvnw package'
                }
            }
        }
    }

    post {
        always {
            // Optional: archive the Jacoco report and artifacts
            archiveArtifacts '**/target/*.jar'
            junit '**/target/test-*.xml'  // For publishing test results
        }
    }
}
