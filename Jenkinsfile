pipeline {
  agent any

  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', 
        url: 'https://github.com/raraduck/source-maven-java-spring-hello-webapp.git'
      }
    }
    stage('Build') {
      steps {
        sh 'echo "Hi"'
      }
    }
    #stage('Test') {
      #steps {
        #sh '<COMMAND>'
      #}
    #}
    #stage('Deploy') {
      #steps {
        #deploy adapters: [tomcat9(credentialsId: '<NAME>', url: '<URL>')], contextPath: null, war: 'path/to/war'
      #}
    #}
  }
}
