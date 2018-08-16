pipeline {
  agent {
         dockerfile true
     }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'sudo npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'sudo npm test'
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
