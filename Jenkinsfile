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
                def registry_url = "registry.hub.docker.com/"
                sh '''
                  docker login -u $USER -p $PASS ${registry_url} '''
                  docker.withRegistry("http://${registry_url}", "dockerhubUNPWD") {
                 sh ''' docker push padmarajug/appslink:latest '''
                  }
               
                }
            }
        }
    }
}
