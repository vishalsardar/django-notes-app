@Library('Shared')_
pipeline{
    agent { label 'vinod'}
    stages{
        stage("Code clone"){
            steps{
                script{
                    clone("https://github.com/vishalsardar/django-notes-app.git","main")
                }
            }
        }
        stage("Code Build"){
            steps{
                script{
                    build("notes-app1","latest")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    push_image("vishalsardar02","notes-app1","latest")
                }
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
