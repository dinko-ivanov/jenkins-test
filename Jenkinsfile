pipeline {
	agent any
	stages {
		stage('build') {
			steps {
				sh './gradlew clean build'
			}
		}
		stage('test') {
			parallel {
			    stage('integration tests') {
					steps {		
					    sleep 5
						echo 'integration tests done'			    
					}
				}
			    stage('performance tests') {
					steps {		
					    sleep 3
						echo 'performance tests done'			    
					}
				}
			}
		}
		stage('deploy') {
		    steps {
				input 'Deploy to production'
     			echo 'deploying ...'     
		    }
		    
		}

	}
}
