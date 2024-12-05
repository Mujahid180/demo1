pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: 'b8967864-20fb-4604-99f8-4d4ef0120e99', path: '', url: 'http://localhost:8080')], contextPath: '/ci-cd', war: '**/*.war' }
 }
 }
 }
}

