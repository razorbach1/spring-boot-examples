pipeline {
  agent {
    node {
      label 'centos7-nodejs'
    }

  }
  stages {
    stage('CheckOutCode') {
      steps {
        cleanWs()
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

    stage('Increment') {
      steps {
        sh '''cd spring-boot-package-war 
mvn build-helper:parse-version versions:set -DnewVersion=0.0.2.$BUILD_ID-SNAPSHOT versions:commit'''
      }
    }

    stage('packege') {
      steps {
        sh '''cd spring-boot-package-war
mvn clean package'''
      }
    }

    stage('Slack') {
      steps {
        slackSend(channel: 'int-project', message: 'Success! Raz', token: 'Z9sGHTKC0iGOYzeIdmOSZwZB')
      }
    }

  }
}