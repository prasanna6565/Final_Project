pipeline{
    agent any
   tools {
       maven 'maven'
       jdk 'Java'
   }
    environment {
        dockerhub=credentials('dockerhub')
        
    }
    stages{
        stage('clean')
        {
            steps{
                sh 'mvn clean'
            }
        }

        stage('pack')
        {
            when{
                branch "prod"
                }
            steps{
                sh 'mvn package -DskipTests'
            }
        }
       stage('build image')
        {
            when{
                branch "prod"
                }
            steps{
                sh 'docker build -t capstone-img:1.01 .'
            }
        } 

//         
//         stage('deploy')
//         {
//             when{
//                 branch "prod"
//                 }
//             steps{
//                 script{
//                    kubernetesDeploy configs: '**/appdeploy.yaml', kubeConfig: [path: ''], kubeconfigId: 'kubeconfig', secretName: '', ssh: [sshCredentialsId: '*', sshServer: ''], textCredentials: [certificateAuthorityData: '', clientCertificateData: '', clientKeyData: '', serverUrl: 'https://']
//                 }
//             }
        }
        
    }





