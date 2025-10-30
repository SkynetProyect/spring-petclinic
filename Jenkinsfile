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
        sh 'mvn clean install -DskipTests'
        // Guarda los JARs generados para usarlos luego
        stash includes: 'target/*.jar', name: 'app-jar'
      }
    }

    stage('Docker Build') {
      agent any
      steps {
        // Recupera el .jar generado en el stage anterior
        unstash 'app-jar'
        sh '''
          ls -l target/
          docker build -t leninospina/spring-petclinic:latest .
        '''
      }
    }
  }
}
