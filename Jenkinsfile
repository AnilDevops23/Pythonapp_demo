pipeline {
    agent any
    stages {
            stage('Checkout the code from SCM') {
                steps {
                   git branch: 'main', url: 'https://github.com/AnilDevops23/Pythonapp_demo'
                }
            }

            stage('Build and Push Docker Image') {
          environment {
            DOCKER_IMAGE = "anildevops23/pythonapp:${BUILD_NUMBER}"
            // DOCKERFILE_LOCATION = "java-maven-sonar-argocd-helm-k8s/spring-boot-app/Dockerfile"
            REGISTRY_CREDENTIALS = credentials('dockerhub')
          }
          steps {
            script {
                sh 'docker build -t ${DOCKER_IMAGE} .'
                def dockerImage = docker.image("${DOCKER_IMAGE}")
                docker.withRegistry('https://index.docker.io/v1/', "dockerhub") {
                    dockerImage.push()
                }
            }
          }
        }
    }
}
