pipeline {
  agent {
    kubernetes {
      label 'cloud-run'
      yamlFile 'pod.yml'
    }
  }
  options { 
    buildDiscarder(logRotator(numToKeepStr: '4'))
    preserveStashes(buildCount: 4)
  }
  stages {
    stage('Cloud Run Deploy') {
      steps {
        container('gcp-sdk'){
          sh 'gcloud beta run deploy bee-cd --image gcr.io/core-workshop/bee-cd:65 --allow-unauthenticated --platform managed --region us-east1'
          sh 'gcloud beta run services describe bee-cd --platform managed --region us-east1'
          sh 'curl https://bee-cd.cb-sa.io'
          //sh 'gcloud --quiet beta run services delete bee-cd --platform managed --region us-east1'
          //sh 'gcloud beta run deploy bee-cd --image gcr.io/core-workshop/bee-cd:65 --platform gke --namespace cloud-run --cluster core-labs-cb-sa	--cluster-location us-east4-b	--connectivity external'
          //sh 'gcloud --quiet beta run services delete bee-cd --platform gke --cluster core-labs-cb-sa	--cluster-location us-east4-b'
        }
      }
    }
  }
}
