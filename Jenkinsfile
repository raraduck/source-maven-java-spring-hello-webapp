pipeline {
  agent any

  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage('Parallel Job') {
	parallel {
	    stage('Parallel1: Checkout') {
	      steps {
		git branch: 'main', 
		url: 'https://github.com/raraduck/source-maven-java-spring-hello-webapp.git'
	      }
	    }
	    stage('Build') {
	      steps {
		sh 'mvn clean package'
	      }
	    }
	}
	parallel {
	    stage('Parallel2: Test') {
	      steps {
		echo 'parallel2'
	      }
	    }
	}
    }
  }
}
