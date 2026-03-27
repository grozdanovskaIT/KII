pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                echo 'Repository cloned'
            }
        }

        stage('Build image') {
            steps {
                sh 'docker build -t grozdanovskaIT/jenkins-demo:latest .'
            }
        }

        stage('Push image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh '''
                        echo "" | docker login -u "" --password-stdin
                        docker push grozdanovskaIT/jenkins-demo:latest
                    '''
                }
            }
        }
    }
}
