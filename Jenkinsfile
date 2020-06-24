pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh "echo 'echo This is application version $BUILD_NUMBER!' > app.sh"
      }
    }
    
    stage('Test') {
      steps {
        sh "./app.sh"
      }
    }
    
    stage('Deploy to Staging') {
      steps {
        echo "deploying to staging"
      }
    }
    
    stage('Sanity check') {
      input "Deploy to production?"
    }
    
    stage('Deploy to Production') {
      parallel {
        stage('Deploy to Production Saas') {
          steps {
            echo "deploying to production saas"
          }
        }

        stage('Deploy to Production App') {
          steps {
            echo "deploying to production app"
          }
        }
      }
    }
  }
}
