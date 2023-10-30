# https://www.jenkins.io/doc/book/pipeline/jenkinsfile/
pipeline {
  
  agent any #{ docker { image 'docker:dind'; args '--name ${BUILD_TAG}' } }
  
  stages {
    
    stage('Setup') {
      script { 
        properties([
          parameters([
            string(defaultValue: 'devtest', name: 'IMAGE_NAME', trim: true)
          ])])}}
    
    stage('Package') {
      steps {
        docker {
          user 'root'
          volumes_from "${env.BUILD_TAG}"
          image "buildpacksio/pack:latest"
          args "build ${IMAGE_NAME}:${env.BUILD_ID}" --builder paketobuildpacks/builder:base --path '${WORKSPACE}'"
        }}}
    
    stage('Release') {
      steps {
        docker.withRegistry('https://registry.docker.io/v2','denzuko-dockerhub') {
          docker.push("${IMAGE_NAME}:${env.BUILD_ID}")
        }}}
    
  }
}
