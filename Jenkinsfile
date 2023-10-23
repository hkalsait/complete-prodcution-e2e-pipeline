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
        }

        stages {
            stage("Checkout from SCM") {
                steps {
                    echo "Cleaning our workspace..."
                    git branch: "main", credentialsId: "github", url: "https://github.com/hkalsait/complete-production-e2e-pipeline"
                }
            }
        }
}