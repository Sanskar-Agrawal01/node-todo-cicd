@Library("Shared") _
pipeline{
    agent { label 'vinod' }
    
    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code Clone"){
            steps{
                script{
                    clone("https://github.com/Sanskar-Agrawal01/node-todo-cicd.git", "master")
                }
            }
        }
        stage("Code Build & Test"){
            steps{
                script{
                    docker_build("notes-app", "latest", "sanskarag")
                }
            }
        }
        stage("Push To DockerHub"){
            steps{
               script{
                docker_push("notes-app", "latest", "sanskarag")
            }  
            }
        }
        stage("Deploy"){
            steps{
                  sh "docker compose down"
                  sh "docker compose up -d"
            }
        }
    }
}
