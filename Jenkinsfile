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
                script {
                    docker.build("grozdanovskaIT/kii-demo:latest")
                }
            }
        }

        stage('Push') {
            steps {
                script {
                    docker.withRegistry('', 'docker-hub-credentials') {
                        docker.image("grozdanovskaIT/kii-demo:latest").push()
                    }
                }
            }
        }
    }
}
