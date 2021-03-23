pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent any
    stages {
        stage('build and push') {            
            sh "docker-compose up --build"
        }
    }
}
