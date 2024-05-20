pipeline{
    agent any 
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
}
