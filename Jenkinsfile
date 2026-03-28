pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Clone stage'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t grozdanovskaIT/kii-demo:latest .'
            }
        }

        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker push grozdanovskaIT/kii-demo:latest'
                }
            }
        }
    }
}
