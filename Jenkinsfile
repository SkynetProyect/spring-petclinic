#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.9-eclipse-temurin-25'
          args '-v $WORKSPACE:/app'
          reuseNode true
        }
      }
      steps {
        sh 'cd /app && mvn clean install || true'
      }
    }
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t leninospina/spring-petclinic:latest .'
      }
    }
  }
}