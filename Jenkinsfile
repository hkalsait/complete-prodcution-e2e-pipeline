pipeline {
    agent any 

    tools {
        jdk 'Java17'
        maven 'Maven3'
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

            stage("Build Application") {
                steps {
                    sh "mvn clean package"
                }
            }
        
            stage("Test the Application") {
                steps {
                    sh "mvn test"
                }
            }
        }
        
}