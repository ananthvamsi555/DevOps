pipeline{
    agent any

    tools{
        maven 'Maven'
    }
    
    stages{
        stage("Clone repository"){
            steps{
                script{
                    git 'https://github.com/ananthvamsi555/DevOps.git'
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    sh 'mvn clean package'

                }
            }
        }
    }
}
