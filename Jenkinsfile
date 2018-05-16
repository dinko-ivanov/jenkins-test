pipeline {
	agent any
	stages {
	    stage('build') {
	        steps {
	            sh './gradlew clean build'
	        }
	    }
	    stage('tests') {
    	    parallel {
        	    stage('integration tests') {
        	        steps {
        	            sleep time: 3000, unit: 'MILLISECONDS'
        	        }
        	    }
        	    stage('performance tests') {
        	        steps {
        	            sleep time: 2000, unit: 'MILLISECONDS'
        	        }
        	    }
    	    }
	    }
	    stage('deploy') {
	    	steps {
	    		input 'Deploy to production?'
	        	echo 'deploying ...'	    	   
	    	}
	    }

	}
}
