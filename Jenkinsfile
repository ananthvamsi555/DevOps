pipeline {
    agent any
    environment{
        REPO_URL = 'https://github.com/ananthvamsi555/DevOps.git'
        BRANCH_NAME = 'master'
    }
    tools {
        maven 'Maven'  // Reference to the Maven installation in Jenkins
    }

    stages {
        stage("Clone repository") {
            steps {
                scmCheckout(REPO_URL,BRANCH_NAME)
            }
        }

        stage("Build") {
            steps {
                script {
                    bat 'mvn clean package'  // For Windows agents
                    // sh 'mvn clean package'  // For Unix-based agents
                }
            }
        }
    }

    post {
        success {
            // Archive build artifacts
            archiveArtifacts artifacts: '**/target/**/*', allowEmptyArchive: true
        }

        always {
            // Publish JUnit test results
            junit '**/target/surefire-reports/*.xml'
            
            // Publish HTML reports (from Surefire Report Plugin)
            /*
            publishHTML(target: [
                reportName: 'Test Report',
                reportDir: 'target/site', // Directory where HTML reports are generated
                reportFiles: 'index.html', // The main report file
                keepAll: true,
                allowMissing: false
            ])
            */
        }
    }
}
