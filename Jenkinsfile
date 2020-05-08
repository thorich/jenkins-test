pipeline {
  agent any
  stages {
    stage("build") {
      steps {
        echo 'building the application...' + BUILD_NUMBER
      }
    }
    stage("test") {
      when {
        expression {
          echo 'Branch name ' + BRANCH_NAME
          BRANCH_NAME == 'dev'
        }
      }
      steps {echo 'testing application...'}
    }
    stage("deploy") {
      steps { echo 'deploying application...'}
    }
  }

  post {
    always {
      echo 'the pipeline is done'
    }
    success {
      echo '...and finished successfully'
    }
    failure {
      echo '...but failed'
    }
  }
}
