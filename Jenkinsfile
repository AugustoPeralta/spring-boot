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
            waitForQualityGate()
          }
        }
      }
    }
  }
  tools {
    maven 'maven'
  }
}