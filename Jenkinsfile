pipeline {
  agent any
  stages {
    stage('Build front-end') {
      steps {
        git 'https://github.com/microservices-demo/front-end.git'
        script {
          def customImage = docker.build registry + ":latest"
          docker.withRegistry( '', registryCredential ) {
            customImage.push()
          }
          sh "docker rmi $registry:latest"
        }

      }
    }

    stage('Test') {
      steps {
        echo 'No tests'
      }
    }

    stage('Deploy') {
      steps {
        git 'https://github.com/dvyakimov/microservices-demo.git'
        dir(path: 'deploy/kubernetes/') {
          script {
            kubernetesDeploy(configs: 'complete-demo.yaml', kubeconfigId: "kubeconfig")
          }

        }

      }
    }

  }
  environment {
    registry = 'dvyakimov/front-end'
    registryCredential = 'dvyakimov'
  }
}