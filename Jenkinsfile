pipeline{
    agent any
    stages {
        stage('run Test'){
            steps{
                sh "docker-compose up"
            }
        }
        stage('Bring Grid Down'){
            steps{
                sh "docker-compose down"
            }
        }
    }
}