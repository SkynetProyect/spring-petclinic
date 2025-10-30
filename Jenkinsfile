#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.9-eclipse-temurin-25'
          args '-v /var/jenkins_home/workspace/spring-pletclinic-docker:/app'
          reuseNode true
        }
      }
      steps {
        sh '''
          cd /app
          mvn clean install -DskipTests
          echo "📦 Contenido del directorio target:"
          ls -l target || echo "⚠️ target no existe"
          docker build -t leninospina/spring-petclinic:latest .
        '''
      }
      
    }

  }
}