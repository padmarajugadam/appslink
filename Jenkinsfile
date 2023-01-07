pipeline {
   agent any
    stages {
        stage ( 'docker build' ) {
            steps {
                sh '''docker build . -t  padmarajug/appslink:latest'''
            }
        }
        stage ( 'push image' ) {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhubUNPWD', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
               // def regUrl = "index.docker.io"
                sh '''
                  docker login -u $USER -p $PASS index.docker.io 
                  docker push padmarajug/appslink:latest
                '''
                }
            }
        }
    }
}
