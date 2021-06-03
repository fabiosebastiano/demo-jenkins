pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'TEST MESSAGE'
      }
    }

    stage('Test') {
      parallel {
        stage('Linux Test') {
          steps {
            echo 'Run LINUX test'
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
  post {
    always {
      archiveArtifacts(artifacts: 'target/artefatto.jar', fingerprint: true)
    }

    failure {
      mail(to: 'fsebastiano@gmail.com', subject: "Failed Pipeline ${currentBuild.fullDisplayName}", body: " For details about the failure, see ${env.BUILD_URL}")
    }

  }
}