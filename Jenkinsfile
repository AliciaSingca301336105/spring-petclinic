pipeline {
    agent any

    triggers {
<<<<<<< HEAD
        cron('H/3 * * * 1')  // Trigger every 3 minutes on Mondays
=======
        cron('H 0/3 * * * 1')  // Trigger every 3 minutes on Mondays
    }

    environment {
        // Define any environment variables here if needed
>>>>>>> 855dccc8413fb91999e50f72d348d2d92354c7f0
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
