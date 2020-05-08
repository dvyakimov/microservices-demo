pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
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

        stage('Build payment') {
          steps {
            git 'https://github.com/microservices-demo/payment.git'
            sh '''def customImage = docker.build registry + ":latest"
docker.withRegistry( \'\', registryCredential ) {
customImage.push()
}
sh "docker rmi $registry:latest"'''
          }
        }

        stage('Build carts') {
          steps {
            git 'https://github.com/microservices-demo/carts.git'
            sh '''def customImage = docker.build registry + ":latest"
docker.withRegistry( \'\', registryCredential ) {
customImage.push()
}
sh "docker rmi $registry:latest"'''
          }
        }

        stage('Build catalodue') {
          steps {
            git 'https://github.com/microservices-demo/catalogue.git'
            sh '''def customImage = docker.build registry + ":latest"
docker.withRegistry( \'\', registryCredential ) {
customImage.push()
}
sh "docker rmi $registry:latest"'''
          }
        }

        stage('Build orders') {
          steps {
            git 'https://github.com/microservices-demo/orders.git'
            sh '''def customImage = docker.build registry + ":latest"
docker.withRegistry( \'\', registryCredential ) {
customImage.push()
}
sh "docker rmi $registry:latest"'''
          }
        }

        stage('Build shipping') {
          steps {
            git 'https://github.com/microservices-demo/shipping'
            sh '''def customImage = docker.build registry + ":latest"
docker.withRegistry( \'\', registryCredential ) {
customImage.push()
}
sh "docker rmi $registry:latest"'''
          }
        }

        stage('Build queue-master') {
          steps {
            git 'https://github.com/microservices-demo/queue-master.git'
            sh '''def customImage = docker.build registry + ":latest"
docker.withRegistry( \'\', registryCredential ) {
customImage.push()
}
sh "docker rmi $registry:latest"'''
          }
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