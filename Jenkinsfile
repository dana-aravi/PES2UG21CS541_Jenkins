pipeline {
  agent any
  stages {
    stage('Clone repository') {
      steps {
        checkout([$class:'GitSCM',
          branches: [[name: '*/main']],
          userRemoteConfigs: [[url: 'https://github.com/dana-aravi/PES2UG21CS541_Jenkins.git']]])
      }
    }
    stage('Build') {
      steps {
        build 'PES2UG21CS541-1'
        sh 'g++ hello.cpp -o output'
      }
    }
    stage('Test') {
      steps {
        // Introduce an intentional error in the test stage
        sh './output.sh'
      }
    }
    stage('Deploy') {
      steps {
        echo 'deploy'
      }
    }
  }
  post {
    failure {
      error 'Pipeline failed'
    }
  }
}
