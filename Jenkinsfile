pipeline {
  agent any
  options { timestamps() }
  triggers { pollSCM('H/5 * * * *') }
  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/AboubacarCamara868/projetJenkins.git', branch: 'main'
        bat 'git status'
      }
    }
    stage('Build') {
      steps {
        bat 'echo === Build : preparation du livrable ==='
        bat 'if exist dist rmdir /s /q dist'
        bat 'mkdir dist'
        bat 'copy index.html dist\\'
        bat 'copy style.css dist\\'
        bat 'dir dist'
      }
    }
    stage('Test') {
      steps {
        bat 'echo === Test : verification des fichiers ==='
        bat 'if not exist dist\\index.html exit 1'
        bat 'if not exist dist\\style.css exit 1'
        bat 'findstr /C:"<h1>" dist\\index.html'
        bat 'echo Tests OK'
      }
    }
    stage('Delivery') {
      steps {
        bat 'echo === Delivery : livraison ==='
        archiveArtifacts artifacts: 'dist/**', fingerprint: true
        bat 'echo Le site est pret a etre affiche'
      }
    }
  }
  post {
    success { echo 'Build OK' }
    failure { echo 'Build KO' }
  }
}