
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

parallel unitAndIntegration : {
	runTests("unitAndIntegrationTests")                                
}, e2e : {
	runTests("e2eTests")
}, performance: {
	runTests("performanceTests")
}

def runTests(tests) {
	node {
		unstash 'everything'
		bat "gradlew test --tests *.${tests}"    
	}

}


