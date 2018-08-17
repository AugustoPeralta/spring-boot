pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/AugustoPeralta/spring-boot.git', branch: 'master')
      }
    }
    stage('build') {
      parallel {
        stage('build') {
          steps {
            sh 'mvn clean package'
          }
        }
        stage('Sonarqube-Analisis') {
          steps {
             withSonarQubeEnv('sonar') {
              // requires SonarQube Scanner for Maven 3.2+
              sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.3.0.603:sonar'
          }
        }
      }
    }
  }
  tools {
    maven 'maven'
  }
}
