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

    stage('Docker Image Push') {
      steps {
        script {
          docker.withRegistry("", "dockerhub-id") {
            docker.image("${registry}:latest").push("latest")
          }
        }

      }
    }

  }
  environment {
    registry = 'serhiidubovchuk/flask-app'
  }
}