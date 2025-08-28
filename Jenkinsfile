pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package -DskipTests'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                }
            }
        }

        stage('Deploy') {
            steps {
                // Example: deploy to a Maven repo, Tomcat, or remote server
                sh 'mvn deploy -DskipTests'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed: Compile → Test → Package → Deploy successful!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
