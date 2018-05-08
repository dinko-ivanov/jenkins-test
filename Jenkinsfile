pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat 'gradlew clean build -x test'
      }
    }
    stage('tests') {
	    parallel {
			stage('unit and integration tests') {		                                
				steps {
	        		bat 'gradlew test --tests *.unitAndIntegrationTests'
	      		}
			}
			stage('e2e tests') {		                                
				steps {
	        		bat 'gradlew test --tests *.e2eTests'
	      		}
			}
			stage('performance tests') {		                                
				steps {
	        		bat 'gradlew test --tests *.performanceTests'
	      		}
			}
	    }
	}
  }
}