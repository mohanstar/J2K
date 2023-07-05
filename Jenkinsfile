pipeline {
        agent any
  environment {
        registry = "mohankt/j2k:1.0.0"
        registryCredential = 'DockerHubCreds' 
  }

  stages {

    stage('Checkout Source') {
      steps {
        git branch: 'main', url: 'https://github.com/gitqprofiles/J2K.git'
      }
    }

  /*  stage('Build image') {
      steps{
        script {
          dockerImage = docker.build registry
        }
      }
    }

    stage('Pushing Image') {
      environment {
               registryCredential = 'DockerHubCreds'
           }
      steps{
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    } */

    stage('Deploying React.js container to Kubernetes') {
      steps {
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
          //docker pull mohankt/j2k:1.0.0
          }
               sh "kubectl get nodes"
         // sh "kubectl apply -f deployment.yaml"
          // sh "kubectl apply -f service.yaml"
        }
      }
    }

  }
}
