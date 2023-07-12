node {
  def app
  
  stage('Clone Repo') {
    checkout scm
    
  }

  stage('Update Repo') {
    script {

      catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
        withCredentials([usernamePassword(credentialsId: 'GIT_HUB_CREDENTIALS', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
          

          sh 'git config credentials.helper "/opt/helper.sh"'
          sh "cat deployment/deployment.yaml"
          sh "sed -i 's+x64nik/argo-flask-apps.*+x64nik/argo-flask-apps:${DOCKERTAG}+g' deployment/deployment.yaml"
          sh "cat deployment/deployment.yaml"
          sh "git add ."
          sh "git commit -a -m 'By Jenkins Job cicd-flask-test1-deploy:${env.BUILD_NUMBER}'"
          sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/cicd-flask-test-k8manifest.git" 
        } 
      }
    }
  }
}
