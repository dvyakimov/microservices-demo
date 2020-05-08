pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git 'https://github.com/microservices-demo/front-end.git'
        script {
          def customImage = docker.build("front-end")
          customImage.push()
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
}
