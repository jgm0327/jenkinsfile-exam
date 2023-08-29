pipeline {
    agent any

    stages {
	stage('Checkout') {
            steps {
                git branch: 'main',
		url: https://github.com/jgm0327/source-maven-java-spring-hello-webapp.git
            }
        }
	
	stage('Build') {
            steps {
                sh 'mvn clean package'
            }
  	}
	
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://ec2-43-201-71-134.ap-northeast-2.compute.amazonaws.com:8081')], contextPath: null, war: 'target/hello-world.war'
            }
        }
    }
}
