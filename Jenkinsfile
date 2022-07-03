pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
                git branch: 'war', url: 'https://github.com/Dnesrk/maven.git'
            }
        }
		       stage('build') {
            steps {
                bat 'mvn clean'
                bat 'mvn install'				
				
            }
        }
		stage('deployment') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'webserver', path: '', url: 'http://localhost:8080/manager/html')], contextPath: 'demopipeline', war: '**/*.war'				
				
            }
        }
    }
}
