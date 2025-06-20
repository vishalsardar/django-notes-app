@Library('Shared')_
pipeline{
    agent { label 'vinod'}
    stages{
        stage("Hello Jenkins"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code clone"){
            steps{
                sh "whoami"
                clone("https://github.com/vishalsardar/django-notes-app.git","main")
            }
        }
        stage("Code Build"){
            steps{
                build("notes-app1","latest")
            }
        }
        stage("Push to DockerHub"){
            steps{
                push("vishalsardar02","notes-app1","latest")
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploy stage"
                sh 'docker compose up -d'
            }
        }
        
    }
}
