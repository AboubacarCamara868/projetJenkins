pipeline {
  agent any
  options { timestamps() }
  stages {
    stage('Cloner le depot') {
      steps {
        git url: 'https://github.com/AboubacarCamara868/projetJenkins.git', branch: 'main'
      }
    }
    stage('Etape 1 : Verification du depot') {
      steps {
        bat 'echo === Etape 1 : Verification du depot ==='
        bat 'git status'
      }
    }
    stage('Etape 2 : Afficher le contenu du projet') {
      steps {
        bat 'echo === Etape 2 : Afficher le contenu du projet ==='
        bat 'dir'
      }
    }
    stage('Etape 3 : Simuler un deploiement local') {
      steps {
        bat 'echo === Etape 3 : Simuler un deploiement local ==='
        bat 'echo Le fichier index.html est pret a etre affiche'
      }
    }
    stage('Etape 4 : Fin du build') {
      steps {
        bat 'echo === Etape 4 : Fin du build ==='
        bat 'echo SUCCESS'
      }
    }
  }
  post {
    success { echo 'Build OK' }
    failure { echo 'Build KO' }
  }
}