pipeline{
    agent any
    stages{
        stage('Build package') {
        steps {
              bat 'mvn clean package'
            
        }
    
        post{
        sucess {
            echo "Archieving the artifacts"
            archieveArtifacts artifacts: '**/*.war'
        }
     }
    }
}
 }
