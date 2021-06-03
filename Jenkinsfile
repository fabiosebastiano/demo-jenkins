pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'TEST MESSAGE'
        sh 'sh run_build_script.sh'
      }
    }

    stage('Test') {
      parallel {
        stage('Linux Test') {
          steps {
            echo 'Run LINUX test'
            sh 'sh run_linux_tests.sh'
          }
        }

        stage('Windows Test') {
          steps {
            echo 'Run WINDOWS tests'
          }
        }

      }
    }

    stage('Deploy Staging') {
      steps {
        echo 'Deploy to staging environment'
        input 'Ok to deploy to production?'
      }
    }

    stage('Deploy Production') {
      steps {
        echo 'Deploy to Prod'
      }
    }

  }
}