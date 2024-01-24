pipeline {
  agent any

  environment {
    def mvn = tool 'M3';
  }

  stages {
    stage('SCM') {
      steps {
        checkout scm
      }
    }
    
    stage('Compile') {
      steps {
        script {
          sh "${mvn}/bin/mvn compile"
        }
      }
    }

    stage('SonarQube Analysis') {
      steps {
        withSonarQubeEnv('sonar-server') {
          sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=toto-gros -Dsonar.projectName='toto-gros'"
        }
      }
    }
  }
}
