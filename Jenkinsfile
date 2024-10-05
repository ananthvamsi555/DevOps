pipeline{
    agent any 
    tools {
        maven 'Maven'
    }
    stages{
        stage("Clone repository"){
            steps{
                git 'https://github.com/ananthvamsi555/DevOps.git'
            }
        }
        stage("Build"){
            steps{
                bat 'mvn clean package'        
            }
        }
    }

      post {
      always {
        junit '**/target/surefire-reports/*.xml'
        cleanWs()
      }
   } 
    
}
