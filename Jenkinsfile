pipeline {
 environment {
 imagename = “flashpratik/jenkins-docker”
 registryCredential = ‘flashpratik-dockerhub’
 dockerImage = ‘’
 }
 agent any
 stages {
 stage(‘Cloning git’) {
 steps{
 git([url: ‘https://github.com/PratikChavhan99/Simplilearn.git', branch: ‘main’])    
 }
 }
 stage(‘Building image’) {
 steps{
 script {
 dockerImage = docker.build imagename
 }
 }
 }
 stage(‘Running image’) {
 steps{
 script {
 sh “docker run ${imagename}:latest”
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
