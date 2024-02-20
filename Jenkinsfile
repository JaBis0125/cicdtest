pipeline {
  agent any
  stages {
    stage('git scm update'){
      steps {
        git url: 'https://github.com/JaBis0125/cicdtest.git', branch: 'main'
      }
    }
    stage('docker build and push')
      steps {
        sh '''
        docker build -t 211.183.3.199
        docker push 211.183.3.199
        '''
      }
  }
  stage('deploy kubernetes')
    steps {
      sh '''
      kubectl create deployment pl-bulk-prod --image=211
