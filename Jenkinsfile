pipeline {
   agent any
    stages {
        stage ( 'docker build' ) {
            steps {
                sh '''docker build . -t  padmarajug/appslink:1.0'''
            }
        }
        stage ( 'push image' ) {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhubUNPWD', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                sh '''
                  docker login -u $USER -p $PASS registry.hub.docker.com/
                  docker push padmarajug/appslink:1.0 '''
                  
               
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

