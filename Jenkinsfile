node('built-in')
{
   stage('ContinusDownloads')
  {
      git 'https://github.com/AkashB1993/Maven2.git'
      
  }
   stage('ContinusBuild')
  {
      sh 'mvn package'
  }
  stage('ContinuousDeploy')
  {
     deploy adapters: [tomcat9(credentialsId: '14913ee1-760e-42cd-bd05-0d981085ad17', path: '', url: 'http://172.31.8.235:8080')], contextPath: 'akash', war: '**/*.war' 
  }
   stage('ContinusTesting')
  {
     git 'https://github.com/AkashB1993/functionaltesting.git'
     sh 'java -jar  /home/ubuntu/.jenkins/workspace/mutipbranch/testing.jar'   
  }
  stage('continuousDelivary')
  {
     // input message: 'production fail plz ckh', submitter: 'akash'
       deploy adapters: [tomcat9(credentialsId: '14913ee1-760e-42cd-bd05-0d981085ad17', path: '', url: 'http://172.31.1.26:8080')], contextPath: 'borade', war: '**/*.war' 
  }
}
