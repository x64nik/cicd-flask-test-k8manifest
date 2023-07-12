node {
  def app
  
  stage('Clone Repo') {
    checkout scm

  }

  stage('Update Deployment file') {
    sshagent(['git_ssh_key']) {
      sh "echo ok"
    }
  }

}
