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
                stage('Parallel2: Test') {
                    steps {
                        echo 'parallel2'
                    }
                }
            }
        }
		stage('Build') {
			steps {
				sh 'mvn clean package -DskipTests=true'
			}
		}
		stage('Deploy') {
			steps {
				deploy adapters: [tomcat9(credentialsId: 'tomcat-manager', path: '', url: 'http://3.38.205.251:8080/')], contextPath: null, war: 'target/hello-world.war'
			}
		}
    }
}