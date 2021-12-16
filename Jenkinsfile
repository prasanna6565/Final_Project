pipeline {
   agent any

   tools {
       maven 'maven'
       jdk 'Java'
   }
   environment {
      dockerhub=credentials('dockerhub')
   }
   environment {
      dockerhub=credentials('dockerhub')
   }
   stages{
       stage("clean"){
      
         steps
            {
                sh 'mvn clean'
            }
       }

   stage("packaging"){
      when{
             branch 'prod'
          }
            {

                sh 'mvn package -DskipTests'
            }

   }
      stage("building docker image"){
       when{
             branch 'prod'
          }
        steps
      
        {
          sh 'docker build -t naincykumari123/capstone:${GIT_COMMIT} . '
        }
      }
         stage('pushing docker image'){
          when{
             branch 'prod'
          }
      
        steps{
          sh '''
          echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin
          docker push naincykumari123/capstone:${GIT_COMMIT} 
          docker logout
          '''

        }
      }
    }
           
        
       }
   

