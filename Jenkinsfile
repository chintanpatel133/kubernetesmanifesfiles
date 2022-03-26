pipeline {
  agent any

  stages {
  
   stage('Checkout Code') {
      steps {
        git branch: 'master',
          url: 'https://github.com/chintanpatel133/kubernetesmanifesfiles.git'
      }
    }
   
   stage('Update GIT Repo') {
      steps {
        script {
          sh "git config user.email chintanpatel671@gmail.com"
          sh "git config user.name Chintan Patel"
          sh "cat deployment.yaml"
          sh "sed -i 's+demo.*+demo:${DOCKERTAG}+g' deployment.yaml"
          sh "cat deployment.yaml"
          sh "git add ."
          sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
          sh "git push origin main"
        }   
      }
   }
  }
}
