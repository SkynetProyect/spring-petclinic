#!groovy
pipeline {
  agent any
  stages {
    stage('Maven Install') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Build Docker image') {
      steps {
        sh 'docker build -t <docker-username>/spring-petclinic:latest .'
      }
    }
  }
}