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
                sh '''
                  docker login -u $USER -p $PASS registry.hub.docker.com/
                  docker push padmarajug/appslink:latest '''
                  
               
                }
            }
        }
	stage ('clean') {
	 steps {
	 cleanWs()
	 }
	}
    }
}

