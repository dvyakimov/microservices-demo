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
        dir(path: 'home/ubuntu') {
          echo 'Deploying'
          sh 'pwd'
          script {
            kubernetesDeploy(configs: 'complete-demo.yaml', kubeconfigId: "kubeconfig")
          }

        }

      }
    }

  }
}