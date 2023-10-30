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
          def customImage = docker.build("${registry}:latest")
          customImage.inside{ c->
          sh './scripts/build.sh'
        }
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
        docker build -t mybuildimage
      }

    }
  }

}
environment {
  registry = 'serhiidubovchuk'
}
}