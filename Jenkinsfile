pipeline {
  agent any

  stages {
    stage("Code") {
      steps {
        echo "cloning the code"
      }
    }
    stage("Build") {
      steps {
        echo "building the code"
      }
    }
    stage("Push to Docker Hub") {
      steps {
        echo "pushing image to dockerhub"
      }
    }
    stage("Deploy") {
      steps {
        echo "deploying the container"
      }
    }
  }
}
