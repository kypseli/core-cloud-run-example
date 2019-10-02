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
          sh 'gcloud info'
          sh 'gcloud beta run deploy bee-cd --image gcr.io/core-workshop/bee-cd:65 --allow-unauthenticated --platform managed --region us-east1'
        }
      }
    }
  }
}
