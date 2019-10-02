pipeline {
  agent {
    kubernetes {
      label 'cloud-run'
      yamlFile 'pod.yml'
    }
  }
  stages {
    stage('Cloud Run Deploy') {
      steps {
        container('gcp-sdk'){
          sh 'echo test'
        }
      }
    }
  }
}
