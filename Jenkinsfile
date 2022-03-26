pipeline {
  agent any

  stages {

    stage('Checkout Code') {
      steps {
        git branch: 'main',
          url: 'https://github.com/chintanpatel133/kubernetesmanifesfiles.git'
      }
    }

    stage('Update GIT Repo') {
      steps {
        script {
          withCredentials([usernamePassword(credentialsId: 'GitHub', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
            sh "git config user.email chintanpatel671@gmail.com"
            sh "git config user.name Chintan Patel"
            sh "cat deployment.yaml"
            sh "sed -i 's+mydevopstechlabs.jfrog.io/mydevopstechlabs-backend-release-local/com.mydevopstechlabs.hms/demo.*+mydevopstechlabs.jfrog.io/mydevopstechlabs-backend-release-local/com.mydevopstechlabs.hms/demo:${DOCKERTAG}+g' deployment.yaml"
            sh "cat deployment.yaml"
            sh "git add ."
            sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
            sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifesfiles.git HEAD:main"
          }
        }
      }
    }
  }
}
