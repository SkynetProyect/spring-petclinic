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
        sh 'mvn clean install -DskipITs'
      }
    }
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t <docker-username>/spring-petclinic:latest .'
      }
    }
  }
}