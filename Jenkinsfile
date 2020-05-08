pipeline {
  agent { dockerfile true }
  stages {
    stage("build") {
      steps {
        echo 'building the application...' + BUILD_NUMBER
      }
    }
    stage("test") {
      when {
        expression {
          BRANCH_NAME == 'master'
        }
      }
      steps {
        echo 'testing application...'
        echo 'Branch name ' + BRANCH_NAME

        sh 'node --version'
        sh 'svn --version'
      }
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
