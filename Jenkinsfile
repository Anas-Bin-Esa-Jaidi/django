@Library("shared") _
pipeline {
    agent any

    stages {
        stage ("hello") {
            steps {
                script {
                    hello()
                }
            }
        }
        stage ("code") {
            steps {
                script {
                    clone("https://github.com/Anas-Bin-Esa-Jaidi/django.git","main")
                }
            }
        }
        stage ("Build") {
            steps {
                script {
                    sh "ls -l"   // debug: confirm Dockerfile exists
                    docker_build("notes-app","latest","anasbinesa275")
                }
            }
        }
        stage ("Test") {
            steps {
                echo "Code is being tested"
            }
        }
        stage ("push") {
            steps {
                script {
                    docker_push("notes-app","latest","anasbinesa275")
                }
            }
        }
        stage ("Deploy") {
            steps {
                echo "code is deployed"
                sh "docker compose up -d"
            }
        }
    }
}
