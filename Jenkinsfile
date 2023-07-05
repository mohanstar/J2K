pipeline {
        agent any
  environment {
        registry = "mohankt/j2k:1.0.0"
        registryCredential = 'DockerHubCreds' 
  }

  stages {

   /* stage('Checkout Source') {
      steps {
        git branch: 'main', url: 'https://github.com/mohanstar/J2K.git'
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

stage('Kubernetes Authentication') {
  steps {
    withCredentials([usernamePassword(credentialsId: 'k8s-key', usernameVariable: 'KUBE_USER', passwordVariable: 'KUBE_TOKEN')]) {
      sh 'kubectl config set-credentials jenkins --token=${KUBE_TOKEN}'
      sh 'kubectl config set-context jenkins-context --cluster=kubernetes-admin@kubernetes --user=jenkins --namespace=default'
      sh 'kubectl config use-context jenkins-context'
    }
  }
}

    stage('Deploying React.js container to Kubernetes') {
      steps {
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
          //docker pull mohankt/j2k:1.0.0
          }
               sh "kubectl apply -f deployment.yaml"
               sh "kubectl apply -f service.yaml"
        }
      }
    }

  }
}
