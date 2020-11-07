pipeline {
	
    agent { label 'master' } 
  	options { buildDiscarder(logRotator(numToKeepStr: '10')) }

    stages {
	     stage('Cleanup ws') {
	     steps {
		    script {
                deleteDir()
       }
	    }
       }    
        stage('Checkout'){
            steps {
                checkout scm
            }
        }
	stage('Install') {
            steps {		    
             sh 'npm install'
            }
        }
        stage('Build') {
            steps {
 		       script{
		echo 'TODO - enable build...'
            }
        }
        }
        stage('Test'){
            steps {
		echo 'TODO - enable unit testing...'
        }
	}
        stage('Artifacts') {
            steps {
 		       script{
		    sh 'zip -r binary.zip *'
            sh "aws s3 cp binary.zip s3://techkibrothers-artifacts-store/${env.BRANCH_NAME}/1.0.${env.BUILD_NUMBER}/"
            }
        }
        }
    }
}
