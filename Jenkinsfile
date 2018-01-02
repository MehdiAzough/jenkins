


pipeline {
    agent any
    tools {
        maven 'Maven 3'
        jdk 'jdk1.8.0_152'
    }
    stages {
        
        stage ('Install') {
            steps {
				bat 'mvn install'
            }
            post {
                success {
                    junit 'target/surefire-reports/*.xml' 
                }
				
            }
        }
		stage ('Package') {
            steps {
				bat 'mvn package'
            }
            post {
                success {
                    junit 'target/surefire-reports/*.xml' 
                }
				
            }
        }
		 stage ('compile') {
            steps {
				bat 'mvn compile'
            }
            post {
                success {
                    junit 'target/surefire-reports/*.xml' 
                }
				
            }
        }
		
		stage ('Site') {
            steps {
				bat 'mvn site'
            }
            post {
                success {
                    junit 'target/surefire-reports/*.xml' 
                }
				
            }
        }

		stage('cobertura'){
			steps{
				bat 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
			}
			post{
				success {
					step([$class: 'CoberturaPublisher', autoUpdateHealth: false, autoUpdateStability: false, coberturaReportFile: 'target/site/cobertura/*.xml', failUnhealthy: false, failUnstable: false, maxNumberOfBuilds: 0, onlyStable: false, sourceEncoding: 'ASCII', zoomCoverageChart: false])
				}
}
		}
		
    }
}

