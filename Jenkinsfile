pipeline{
  agent any
  tools{
    maven 'Maven'
  }
  stages{
    stage ('Initialize'){
      steps{
        sh '''
               echo "PATH=${PATH}"
               echo "M2_HOME=${M2_HOME}"
               
           '''
      }
    }
    
    stage ('Check-Git-Secrets') {
      
      steps {
        sh 'rm trufflehog || true'
        sh 'docker run gesellix/trufflehog --json https://github.com/Tulasiram69/webapp.git > trufflehog'
       
         
      }
    }
      stage ('Build'){
      steps{
      sh 'mvn clean package'
        
      }
     }
   }
 }
