pipeline {
  agent any

  environment {
      def mvn = tool 'M3';
  }
  
  stages {
    stage('SCM') {
      steps{
        checkout scm
      } 
    }
    stage('SonarQube Analysis') {
      steps{
        withSonarQubeEnv('sonar-server') {
        sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=toto-gros -Dsonar.projectName='toto-gros'"
      }
    }
     
  }
 }
}
