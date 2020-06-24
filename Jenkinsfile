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
      steps {
        input "Deploy to production?"
      }
    }
    
    stage('Deploy to Production') {
      parallel {
        stage('Deploy to Production Saas') {
          stages {
            stage('Deploy') {
              steps {
                echo "deploying to production saas"
              }  
            }
          }
        }
       
        stage('Deploy to Production App') {
          stages {
            stage('Deploy') {
              steps {
                echo "deploying to production app"
              }
            }
          }
        }
      }
    }
  }
}
