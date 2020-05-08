pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'No Build'
      }
    }

    stage('Test') {
      steps {
        echo 'No tests'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying'
        git 'https://github.com/dvyakimov/microservices-demo.git'
        dir ('deploy/kubernetes/') 
          script {
            kubernetesDeploy(configs: 'complete-demo.yaml', kubeconfigId: "kubeconfig")
          }
        }
      }
    }
  }
}
