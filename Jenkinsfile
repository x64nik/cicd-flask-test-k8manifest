node {
  def app
  
  stage('Clone Repo') {
    checkout scm

  }

  stage('Update Deployment file') {
    sshagent(['git_ssh_key']) {
      sh 'cat deployment/deployment.yaml'
      sh 'cat deployment/deployment.yaml'
      sh "sed -i 's+#BuildNo.*+#BuildNo:${DOCKERTAG}+g' deployment/deployment.yaml"
      sh "sed -i 's+x64nik/argo-flask-apps.*+x64nik/argo-flask-apps:${DOCKERTAG}+g' deployment/deployment.yaml"
      sh "cat deployment/deployment.yaml"
      sh "git add ."
      sh "git commit -a -m 'By Jenkins Job cicd-flask-test1-deploy:${env.BUILD_NUMBER}'"
      sh "git push"
    }
  }

}
