pipeline{
    agent any
    environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
    stages{
        
        stage('git clone ') {
            steps{
                echo " https://github.com/prasanna6565/Final_Project.git"
            }
      }

        stage('search') {
            steps{
                sh " docker search centos"
            }
      }

        stage('pulling'){
   
            steps{
                sh " docker pull centos"
            }
      }
       
         stage('list'){
            steps{
                 sh "docker images"
            }
        } 
        stage('docker containers'){
            steps{
                 sh "docker run  centos"
            }
        } 
        stage('docker containers list '){
            steps{
                 sh "docker ps -a"
            }
        } 
        stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		stage('docker image creation'){
            steps{
                 sh "docker commit vigilant_banzai prasannak "
            }
        } 
        	stage('docker new image'){
            steps{
                 sh "docker images "
            }
        } 
        stage('docker tag'){
            steps{
                 sh "docker tag prasannak prasanna2121/prasannak "
            }
        } 
        stage('docker push'){
            steps{
                 sh "docker push prasanna2121/prasannak "
                 echo " succes"
            }
        } 
    }
}
