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
          sh "docker login -u ${user} -p ${pass}"
          sh "docker tag note-app-cicd ${user}/note-app-cicd:latest"
          sh "docker push ${user}/note-app-cicd:latest"
          sh "docker logout"
        }
      }
    }
    stage("Deploy") {
      steps {
        echo "Deploying the container"
        // sh "docker run -d -p 8000:8000 mohammedatique/note-app-cicd:latest"
        sh "docker-compose down && docker-compose up -d"
      }
    }
  }
}
