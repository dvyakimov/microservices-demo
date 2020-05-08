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
          kubernetesDeploy(configs: "/deploy/kubernetes/complete-demo.yaml", kubeconfigId: "kubeconfig")
        }

      }
    }

  }
}