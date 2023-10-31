pipeline {
  agent any
  stages {
    stage('Git checkout') {
      steps {
        script {
          checkout scm
        }

      }
    }

    stage('App Build') {
      steps {
        script {
          sh 'chmod +x ./scripts/build.sh'
          sh './scripts/build.sh'
        }

      }
    }

    stage('Tests') {
      steps {
        script {
          sh 'chmod +x ./scripts/test.sh'
          sh './scripts/test.sh'
        }

      }
    }

    stage('Docker Image Build') {
      steps {
        script {
          docker.build("${registry}:latest")
        }

      }
    }

  }
  environment {
    registry = 'serhiidubovchuk'
  }
}