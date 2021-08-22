pipeline {
  agent {
    node {
      label 'centos7-nodejs'
    }

  }
  stages {
    stage('CheckOutCode') {
      steps {
        git(url: 'https://github.com/razorbach1/spring-boot-examples.git', branch: 'raz_sol', changelog: true)
      }
    }

    stage('maven compile') {
      steps {
        sh '''cd spring-boot-package-war
mvn compile'''
      }
    }

    stage('Test mvn') {
      steps {
        sh '''cd spring-boot-package-war
mvn test'''
      }
    }

  }
}