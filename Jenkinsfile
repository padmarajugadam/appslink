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
                //def registry_url = "registry.hub.docker.com/"
                sh '''
                  docker login -u $USER -p $PASS registry.hub.docker.com/
                  //docker.withRegistry("http://${registry_url}", "dockerhubUNPWD") {
                  docker push padmarajug/appslink:latest '''
                  
               
                }
            }
        }
    }
}

