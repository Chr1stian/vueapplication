pipeline {
  agent {
         docker {
             image 'node:9.11.1-alpine'
             args '-u root -p 3000:80'
         }
     }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'npm test'
            }
        }
      }
}
