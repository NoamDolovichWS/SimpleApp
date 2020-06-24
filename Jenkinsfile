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
    
    stage('Deploy to Production') {
      input "Deploy to production?"
      
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
