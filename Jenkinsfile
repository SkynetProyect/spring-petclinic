#!groovy
#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.9-eclipse-temurin-25'
          // 🔹 Monta el workspace del host Jenkins dentro del contenedor
          args '-v $WORKSPACE:/app -w /app'
          reuseNode true
        }
      }
      steps {
        sh '''
          echo "🚀 Compilando proyecto con Maven..."
          mvn clean install -DskipTests
          echo "📦 Contenido del directorio target:"
          ls -l target || echo "⚠️ No existe el directorio target"
        '''
      }
    }

    stage('Docker Build') {
      agent any
      steps {
        sh '''
          echo "🐳 Construyendo imagen Docker..."
          docker build -t <docker-username>/spring-petclinic:latest .
        '''
      }
    }
  }
}
