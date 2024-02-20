pipeline {
  agent any
  stages {
    stage('git scm update'){
      steps {
        git url: 'https://github.com/JaBis0125/cicdtest.git', branch: 'main'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        docker build -t jabis0125/cicdtest:tagname
        docker push jabis0125/cicdtest:tagname
        '''
      }
  }
  stage('deploy kubernetes') {
    steps {
      sh '''
      kubectl create deployment pl-bulk-prod --image=jabis0125/cicdtest:tagname
      kubectl expose deployment pl-bulk-prod --type=LoadBalancer --port=80
                                             --target-port=80 --name=pl-bulk-prod

        '''
      }
    } 
  }
}
