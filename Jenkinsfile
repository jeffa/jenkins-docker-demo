pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch:'master', url:'https://github.com/jeffa/jenkins-docker-demo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t pipeline:${BUILD_NUMBER} .'
            }
        }
        stage('Deploy') {
            steps {
                //sh 'docker stop webapp_ctr'
                sh 'docker run --rm -d -p 3000:3000 --name webapp_ctr pipeline:${BUILD_NUMBER}'
            }
        }
    }
}
