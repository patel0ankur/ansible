pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Build demo-app'
        sh 'sh run_build_script.sh'
      }
    }

    stage('Linux Tests') {
      parallel {
        stage('Linux Tests') {
          steps {
            echo 'Run Linux tests'
            sh 'sh run_linux_tests.sh'
          }
        }

        stage('Windows Tests Stage') {
          steps {
            echo 'Run Windows Test'
          }
        }

      }
    }

    stage('Deploy Staging') {
      steps {
        echo 'Deploy to staging environment'
        input 'Ok to deploy to prod'
      }
    }

    stage('Deploy to Prod') {
      steps {
        echo 'Deploy to Prod '
      }
    }

    stage('Post Build') {
      steps {
        archiveArtifacts(fingerprint: true, artifacts: 'target/demoapp.jar')
        mail(subject: 'Failed Pipeline ${currentBuild.fullDisplayName}', body: 'For details about the failure, see ${env.BUILD_URL}', cc: 'patel.ankur@live.com')
      }
    }

  }
}