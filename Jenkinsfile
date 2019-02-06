pipeline {
    agent any
    stages {
        stage ('Build Servlet Project') {
            steps {
                /*For windows machine */
               bat  'mvn clean package'

                /*For Mac & Linux machine */
               // sh  'mvn clean package'
            }

            post{
                success{
                    echo 'Now Archiving ....'

                    archiveArtifacts artifacts : '**/*.war'
            }  }
        }
             stage ('Deploy Build in Staging Area'){
            steps{

                build job : 'Deploy-servelet-pipeline'

            }
          }
          stage('Deploy to production'{
              steps{
                  timeout(time:5,units:'Days'){
                      input message: 'Approve Production Deployment'
                  } 
                  build job : 'Deploy-servelet-production-pipeline'
            }
            post{
                success{
                    echo 'Deployment of production is sucessful'
                }
                failure{
                    echo'Deployment of production is failure'
                }
            }
        }  
  }