pipeline {
    agent any

    environment {  /* need to provide your own creds */
        IMAGE_NAME = "aimakovm/cicd-pipeline-aimakovm"
        DOCKER_CREDS = "docker_hub_creds_id"
    }

    stages {

        stage('checkout git') {
            steps {
                checkout scm
            }
        }

        stage('Build stage') {
            steps {
                sh 'scripts/build.sh'
            }
        }

        stage('Tests') {
            steps {
                sh 'scripts/test.sh'
            }
        }

        stage('Image build') {
            steps {
                script {
                    app = docker.build("${IMAGE_NAME}:${BUILD_NUMBER}")
                } 
            }
        }

        stage('Image push') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', DOCKER_CREDS) {
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
                    }
                }
            }
        }
    }
}
