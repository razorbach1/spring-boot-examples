pipeline {
  agent any
  stages {
    stage('CheckOutCode') {
      steps {
        git(url: 'https://github.com/razorbach1/spring-boot-examples.git', branch: 'raz_sol', changelog: true)
      }
    }

  }
}