pipeline {
  agent {
         dockerfile {
          filename 'Dockerfile'
          additionalBuildArgs '-u root'
         }
     }
      stages {
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
