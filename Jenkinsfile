pipeline {
    agent any 

    tools {
        jdk 'Java17'
        maven 'Maven3'
    } 
    environment {
        APP_NAME = "complete-prod-pipeline"
        RELEASE = "1.0.0"
        DOCKER_USER = "hkalsait"
        DOCKER_PASS = "dokerhub"
        IMAGE_NAME = "${DOCKER_USER}" + "/" + "${APP_NAME}"
        IMAGE_TAG = "${RELEASE}-${BUILD_NUMBER}"
    }

        stages {
            stage("Cleanup Workspace") {
                steps {
                    echo "Cleaning our workspace..."
                    cleanWs()
                }
            }

            stage("Checkout from SCM") {
                steps {
                    echo "Cleaning our workspace..."
                    git branch: "main", credentialsId: "github", url: "https://github.com/hkalsait/complete-production-e2e-pipeline"
                }
            }

            /*stage("Build Application") {
                steps {
                    sh "mvn clean package"
                }
            }
        
        stage("Test the Application") {
                steps {
                    sh "mvn test"
                }
            }*/

        }

        stage("Build & Push Docker Image") {
            script{
                docker.withRegistry('',DOCKER_PASS) {
                    docker_image = docker.build "${IMAGE_NAME}"
                }
                docker.withRegistry('',DOCKER_PASS) {
                    docker_image.push("$IMAGE_TAG")
                    docker_image.push('latest')

                }
            }
        }
        
        
}