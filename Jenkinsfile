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
          sh 'pwd'
          git 'https://github.com/dvyakimov/microservices-demo.git'
          script {
            kubernetesDeploy(configs: 'complete-demo.yaml', kubeconfigId: "kubeconfig")
        }
      }
    }

  }
}
