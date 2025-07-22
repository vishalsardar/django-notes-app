@Library('Shared')_
pipeline{
    agent { label 'vinod'}
    parameters{
        string(name:"IMAGE_NAME", defaultValue:"notes-app", description:"Docker Image Name")
        string(name:"IMAGE_TAG", defaultValue:"v1", description:" Docker Image Tag")
    }
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
                    build("${params.IMAGE_NAME}","${params.IMAGE_TAG}")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    push_image("vishalsardar02","${params.IMAGE_NAME}","${params.IMAGE_TAG}")
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
