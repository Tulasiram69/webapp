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
      }
    }
    
     stage ('Source Composition Analysis') {
      steps {
         sh 'rm owasp* || true'
         sh 'wget "https://raw.githubusercontent.com/Tulasiram69/webapp/master/owasp-dependency-check.sh" '
         sh 'chmod +x owasp-dependency-check.sh'
         sh 'bash owasp-dependency-check.sh'
        
        
       }
     }
    
      stage ('Build'){
      steps{
      sh 'mvn clean package'
        
      }
     }
   }
 }
