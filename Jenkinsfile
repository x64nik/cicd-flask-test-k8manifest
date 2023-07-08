node {

    stage("Git Clone"){
            git branch: 'main', credentialsId: 'GIT_HUB_CREDENTIALS', url: 'https://github.com/x64nik/cicd-flask-test.git'
        }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'GIT_HUB_CREDENTIALS', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                    
                    sh "git config user.email rushidarunte123@gmail.com"
                    sh "git config user.name x64nik"
                    //sh "git switch master"
                    //sh "cat deployment.yaml"
                    sh "sed -i 's+x64nik/basic-flask-app:test.*+x64nik/basic-flask-app:${DOCKERTAG}+g' deployment.yaml"
                    sh "cat deployment.yaml"
                    sh "git add ."
                    sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                    sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/cicd-flask-test-k8manifest.git HEAD:argocd"  
                    
      }
    }
  }
}
       

}