#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.9-eclipse-temurin-25'
          reuseNode true
        }
      }
      steps {
        sh '''
          pwd
          ls -la
          mvn clean install -DskipTests
          echo "📦 Contenido del directorio target:"
          ls -l target || echo "⚠️ target no existe"
          docker build -t leninospina/spring-petclinic:latest .
        '''
      }
      
    }

  }
}