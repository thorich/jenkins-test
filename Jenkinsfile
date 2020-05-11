pipeline {
  environment {
    DOCKER_REG = "localhost:5000"
    IMAGE_NAME = "jenkins-test"
    
  }
  agent any
  stages {
    stage("build") {
      steps {
        echo 'building the application...' + BUILD_NUMBER
        sh "docker build -t ${DOCKER_REG}/${IMAGE_NAME}:${BUILD_NUMBER} ."
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
      }
    }
    stage("deploy") {
      steps { 
        echo 'deploying application...'
        sh "docker push ${DOCKER_REG}/${IMAGE_NAME}:${BUILD_NUMBER}"
      }
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
