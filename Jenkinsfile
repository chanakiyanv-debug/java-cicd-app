pipeline {
  agent any
  tools { maven 'maven3' }
  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Build') {
      steps { sh 'mvn clean package' }
    }
    stage('SonarQube Analysis') {
      steps {
        withSonarQubeEnv('sonar') {
          sh 'mvn sonar:sonar -Dsonar.projectKey=java-cicd-app'
        }
      }
    }
  }
}
