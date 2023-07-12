node {
  def app
  
  stage('Clone Repo') {
    checkout scm

  }

  stage('Update Repo') {
    script {

      catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
        withCredentials([string(credentialsId: 'GIT_TOKEN', variable: 'git_token')]) {
          

          sh 'git config credentials.helper "/opt/helper.sh"'
          sh "cat deployment/deployment.yaml"
          sh "sed -i 's+#BuildNo.*+#BuildNo:${DOCKERTAG}+g' deployment/deployment.yaml"
          sh "sed -i 's+x64nik/argo-flask-apps.*+x64nik/argo-flask-apps:${DOCKERTAG}+g' deployment/deployment.yaml"
          sh "cat deployment/deployment.yaml"
          sh "git add ."
          sh "git commit -a -m 'By Jenkins Job cicd-flask-test1-deploy:${env.BUILD_NUMBER}'"
          sh "git push https://${git_token}@github.com/x64nik/cicd-flask-test-k8manifest.git HEAD:argocd" 
        } 
      }
    }
  }
}
