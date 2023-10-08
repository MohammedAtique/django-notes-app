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
        sh("docker build . -t note-app-cicd")
      }
    }
    stage("Push to Docker Hub") {
      steps {
        echo "Pushing image to DockerHub"
        withCredentials([usernamePassword(credentialsId: "dockerHub", usernameVariable: "user", passwordVariable: "pass")]) {
          sh "docker login -u ${env.user} -p ${env.pass}"
          sh "docker logout"
        }
      }
    }
    stage("Deploy") {
      steps {
        echo "Deploying the container"
      }
    }
  }
}
