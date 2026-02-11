pipeline {
  agent any

  environment {
    KEY_PATH = "/var/lib/jenkins/ubuntu.pem"
    NEXT_DEV_OVERLAY= credentials('NEXT_DEV_OVERLAY')
    GITHUB_TOKEN= credentials('GITHUB_TOKEN')
    RESEND_API_KEY= credentials('RESEND_API_KEY')
    NEXT_PUBLIC_GITHUB_USERNAME= credentials('NEXT_PUBLIC_GITHUB_USERNAME')
  }

  stages {

    stage('Install Dependencies') {
      steps {
        sh 'npm install --legacy-peer-deps'
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
          rm -rf /var/www/html/*
          cp -r dist/* /var/www/html/
        '''
      }
    }
  }
}
