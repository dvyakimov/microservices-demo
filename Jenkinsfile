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
        dir ('/home/ubuntu'){
          echo 'Deploying'
          sh 'ls -l'
          script {
            kubernetesDeploy(configs: '/home/ubuntu/complete-demo.yaml', kubeconfigId: "kubeconfig")
          }
        }
      }
    }

  }
}
