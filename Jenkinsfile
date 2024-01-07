pipeline {
 environment {
 imagename = “flashpratik/jenkins-docker”
 registryCredential = ‘flashpratik-docckerhub’
 dockerImage = ‘’
 }
 agent any
 stages {
 stage(‘Cloning Git’) {
 steps {
 git([url: ‘https://github.com/PratikChavhan99/Simplilearn.git', branch: ‘main’])
 }
 }
 stage(‘Building image’) {
 steps{
 script {
 dockerImage = docker.build flashpratik/jenkins-docker
 }
 }
 }
 stage(‘Running image’) {
 steps{
 script {
 sh “docker run ${flashpratik/jenkins-docker}:latest”
 }
 }
 }
 stage(‘Deploy Image’) {
 steps{
 script {
 docker.withRegistry( ‘’, registryCredential ) {
 dockerImage.push(“$BUILD_NUMBER”)
 dockerImage.push(‘latest’)
 }
 }
 }
 }
 }
}
