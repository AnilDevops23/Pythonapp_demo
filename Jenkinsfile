pipeline {
    agent any
    stages {
        stage('Checkout the code from SCM') {
            steps {
               git branch: 'main', url: 'https://github.com/AnilDevops23/Pythonapp_demo'
            }
        }
        stage('Build Docker Image') {
            steps {
               script{
                    sh '''
                    echo 'Buid Docker Image'
                    docker build -t anildevops23/pythonapp:${BUILD_NUMBER} .
                    '''
                }
            }
        }
        stage('Push the artifacts'){
           steps{
                script{
                    sh '''
                    echo 'Push to Repo'
                    docker push anildevops23/pythonapp:${BUILD_NUMBER}
                    '''
                }
            }
        }
    }
}
