pipeline {
    agent any
        
    stages {
        stage ("Code Pull") {
            steps {
                echo "Pulling the code"
                git url: "https://github.com/MohammedAtique072/django-notes-app.git", branch: "test"
            }
        }
        
        stage ("Code Build") {
            steps {
                echo "Building the code"
                sh "docker build . -t django-app-test:latest"
            }
        }
        
        stage ("Pushing Image to DockerHub") {
            steps {
                echo "Pushing the code"
                
                withCredentials([usernamePassword(credentialsId: "dockerhub", passwordVariable: "dpass", usernameVariable: "duser")]) {
                    sh "docker login -u $duser -p $dpass"
                    sh "docker tag django-app-test:latest $duser/django-test:latest"
                    sh "docker push $duser/django-test:latest"
                    sh "docker logout"
                }
            }
        }
        
        stage ("Deploying the code") {
            steps {
                echo "Deploying the Code"
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
