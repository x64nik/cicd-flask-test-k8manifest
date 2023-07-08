node {

    stage("Git Clone"){
            git branch: 'main', credentialsId: 'GIT_HUB_CREDENTIALS', url: 'https://github.com/x64nik/cicd-flask-test.git'
        }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'GIT_HUB_CREDENTIALS', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        
                        sh "echo $GIT_PASSWORD"
                        sh "echo $GIT_USERNAME"
      }
    }
  }
}
       

}