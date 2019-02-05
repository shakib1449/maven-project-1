pipeline{
    agent any
    stages{
        stage('Build package') {
        steps {
              bat 'mvn clean package'
            
        }
    
        post{
        success {
            echo "Archieving the artifacts"
            archieveArtifacts artifacts: '**/*.war'
        }
      }
    }
  } 
 }
