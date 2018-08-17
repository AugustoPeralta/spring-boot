pipeline {
  agent any
  tools {
    maven 'maven'
 }
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/AugustoPeralta/spring-boot.git', branch: 'master')
      }
    }
    stage('build') {
      steps {
        sh 'mvn clean package'
      }
    }
  }

}
