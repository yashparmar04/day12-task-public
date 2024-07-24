pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'Maven 3.9.8' // Ensure this matches your Maven tool name
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git url: 'https://github.com/yashparmar04/day12-task-public.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                // Build the project using Maven
                script {
                    withEnv(["PATH+MAVEN=${MAVEN_HOME}/bin"]) {
                        sh 'mvn clean install'
                    }
                }
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Archive the built artifacts
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
