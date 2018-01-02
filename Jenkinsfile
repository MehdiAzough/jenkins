pipeline {
    agent any
    tools {
        maven 'Maven 3'
        jdk 'jdk1.8.0_152'
    }
    stages {
        
        stage ('Build') {
            steps {
            bat 'mvn install'
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
		stage('Test') {
            steps {              
                sh 'make check || true' 
                junit '**/target/*.xml' 
            }
    }
}