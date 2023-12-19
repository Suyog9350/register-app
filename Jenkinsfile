pipeline{
  agent { label 'Jenkins-Slave' }
  tools{
    jdk 'Java17'
    maven 'Maven3'
  }
  environment{
    APP_NAME = "register-app-pipeline"
    RELEASE = "1.0.0"
    DOCKER_USER = "suyog9350"
    DOCKER_PASS = "dockerhub"
    IMAGE_NAME = "${DOCKER_USER}" + "/" + "${APP_NAME}"
    IMAGE_TAG = "${RELEASE} - ${BUILD_NUMBER}
  }
  stages{
    stage("Cleanup Workspace"){
          steps{
            cleanWs()
          } 
    }

          stage("Checkout from SCM"){
            steps{
              git branch: 'main', credentialsId: 'github', url: "https://github.com/Suyog9350/register-app"
            }
    }
          stage("Build Application"){
                steps{
                  sh "mvn clean package"
                }
          }

          stage("Test Application"){
            steps{
              sh "mvn test"
          }
    }        
  }
}
