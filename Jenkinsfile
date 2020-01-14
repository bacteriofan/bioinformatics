pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn clean test'
      }
    }

    stage('Autotests') {
      steps {
        git(url: 'https://github.com/bacteriofan/brainup.git', branch: 'master', changelog: true, poll: true)
        sh 'mvn clean test'
      }
    }

  }
}