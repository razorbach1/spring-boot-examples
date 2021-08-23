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

    stage('packege') {
      steps {
        sh '''cd spring-boot-package-war
mvn clean package'''
      }
    }

    stage('slack') {
      parallel {
        stage('slack') {
          steps {
            slackSend(token: 'Z9sGHTKC0iGOYzeIdmOSZwZB', channel: 'int-project', message: 'Success!', notifyCommitters: true)
          }
        }

        stage('chuck') {
          steps {
            chuckNorris()
          }
        }

      }
    }

  }
}