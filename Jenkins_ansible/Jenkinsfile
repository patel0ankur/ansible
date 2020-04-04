pipeline {
  agent {
    docker {
      image 'ankurpatel/tomcat'
      args '-p 80:8080'
    }

  }
  stages {
    stage('hello') {
      steps {
        sh '''echo "Hello World"
sudo yum install nginx -y'''
      }
    }
  }
}