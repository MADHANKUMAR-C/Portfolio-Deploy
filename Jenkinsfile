pipeline {
  agent any
  environment {
        KEY_PATH = "/var/lib/jenkins/ubuntu.pem"
    }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/MADHANKUMAR-C/Portfolio-Deploy.git'
      }
    }

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
          sudo cp -r build/* /var/www/html/
        '''
      }
    }
  }
}
