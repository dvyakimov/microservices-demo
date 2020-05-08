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
        script {
          kubernetesDeploy(configs: "complete-deploy.yaml", kubeconfigId: "kubeconfig")
        }

      }
    }

  }
}