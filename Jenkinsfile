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
                if (isUnix)
                {
                    sh 'mvn clean package'
                }
                else{
                    bat 'mvn clean package'
                }

                
            }
        }
    }
}
