pipeline {
  agent any

  environment {
    KEY_PATH = "/var/lib/jenkins/ubuntu.pem"
  }

  stages {

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build React App') {
      steps {
        sh 'npm run build'
      }
    }

    stage('Deploy') {
      steps {
        sh '''
          sudo rm -rf /var/www/html/*
          sudo cp -r dist/* /var/www/html/
        '''
      }
    }
  }
}
