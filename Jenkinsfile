
node {
	
	stage('code checkout') {
		git 'https://github.com/dinko-ivanov/jenkins-test.git'
	}
	
	stage('build') {
	    bat 'gradlew clean build -x test'
	    stash name: 'everything',
	    	  includes: '**'
	}	
}

runTests("unitAndIntegrationTests")                                
runTests("e2eTests")
runTests("performanceTests")

def runTests(tests) {
	node {
		unstash 'everything'
		stage (tests) {
			bat "gradlew test --tests *.${tests}"
		}    
	}

}


