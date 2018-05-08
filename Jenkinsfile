node {
	stage('build') {
	    bat 'gradlew clean build -x test'
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
		bat "gradlew test --tests *.${tests}"    
	}

}


