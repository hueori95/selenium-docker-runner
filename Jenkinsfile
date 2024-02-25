pipeline{
    agent any
    stages {
        stage('Start grid'){
            steps{
                sh "docker-compose -f grid.yaml up -d"
            }
        }
        stage('run test'){
            steps{
                sh "docker-compose -f test-suites.yaml up"
            }
        }
    }

    post{
        always{
            sh "docker-compose -f grid.yaml down"
            sh "docker-compose -f test-suites.yaml down"
            archiveArtifacts artifacts: 'index.html', followSymlinks: false
            archiveArtifacts artifacts: 'output/flight-reservation/emailable-report.html', followSymlinks: false
            archiveArtifacts artifacts: 'output/flight-reservation/index.html', followSymlinks: false
            archiveArtifacts artifacts: 'output/vendor-portal/emailable-report.html', followSymlinks: false
            archiveArtifacts artifacts: 'output/vendor-portal/index.html', followSymlinks: false
        }
    }
}