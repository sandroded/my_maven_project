pipeline {
agent {
  docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
  }
}

  stages {
    stage('checkout') {
      steps {
        git 'https://github.com/sandroded/my_maven_project.git'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean compile'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }
    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }
  }
}
