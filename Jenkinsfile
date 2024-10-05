pipeline {
    agent any

    tools {
        maven 'Maven' // This should reference the Maven installation in Jenkins
    }

    stages {
        stage("Clone repository") {
            steps {
                // Clone the Git repository
                git 'https://github.com/ananthvamsi555/DevOps.git'
            }
        }

        stage("Build") {
            steps {
                // Run Maven clean and package
                script {
                    bat 'mvn clean package'  // For Windows agents
                    // sh 'mvn clean package'  // Use this for Unix-based agents (Linux/macOS)
                }
            }
        }
    }

    post {
        success {
            // Archive the artifacts if the build is successful
            archiveArtifacts artifacts: '**/target/**/*', allowEmptyArchive: true
        }

        always {
            // Publish JUnit test results, if they exist
            junit '**/target/surefire-reports/*.xml'
            
            // Clean the workspace after build
            cleanWs()
        }
    }
}
