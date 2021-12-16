pipeline {
   agent any

   tools {
       maven 'maven'
       jdk 'Java'
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

   stage(‘package’)
{
  when {
    branch 'prod'
  }
    stages{
      stage('building docker image')
      {
        steps
        {
          sh 'docker build -t naincykumari123/capstone:${GIT_COMMIT} . '
        }
      }
      stage('pushing docker image')
      {
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

}
}
