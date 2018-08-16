pipeline {
  agent {
         dockerfile true {
         args: '-u root'
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
        stage('Building image') {
          steps {
            echo 'Build docker image'
            sh 'docker build .'
          }
        }
        stage('Pushing image') {
          steps {
            echo 'Push docker image to server'
          }
        }
      }
}
