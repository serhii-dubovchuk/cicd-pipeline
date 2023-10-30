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
          script scripts/build.sh
        }

      }
    }

  }
  environment {
    registry = 'serhiidubovchuk'
  }
}