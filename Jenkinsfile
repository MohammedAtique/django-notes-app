pipeline {
  agent any

  stages {
    stage("Code") {
      steps {
        echo "Cloning the code"
        git url: "https://github.com/MohammedAtique/django-notes-app.git", branch: "main"
      }
    }
    stage("Build") {
      steps {
        echo "Building the image"
        sh "docker build . -t note-app-cicd"
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
