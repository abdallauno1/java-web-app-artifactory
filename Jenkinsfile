pipeline {
  agent { label 'ubuntu-gui' }
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    CI = true
    ARTIFACTORY_ACCESS_TOKEN = credentials('JFROG-ACCESS-TOKEN')
  }
  
  stages {

    stage('Build') {
       steps {
          sh './mvnw clean install'
        }
    }

    stage('Upload to Artifactory') {
      agent{
         docker {
          image 'releases-docker.jfrog.io/jfrog/jfrog-cli-v2:2.2.0'
          reuseNode true
         }
       }
       steps{
        sh 'jfrog rt upload --url http://localhost:8082/artifactory/java-web-app-artifactory/ --access-token ${ARTIFACTORY_ACCESS_TOKEN} target/demo-0.0.1-SNAPSHOT.jar java-web-app-artifactory/'
       }
    }


  }

  post {
    always {
      sh 'docker logout'
    }
  }

}