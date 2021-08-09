pipeline {
    agent any 
    stages {
        stage('Compile and Clean') { 
            steps {

                sh "mvn clean compile"
            }
        }
       
		stage('Junit5 Test') { 
            steps {

                sh "mvn test"
            }
        }
        
        stage('Deploy') { 
            steps {
                sh "mvn package"
            }
        } 
	
	    stage('Cucumber report') {
		cucumber buildStatus: 'UNSTABLE',
			reportTitle: 'My report',
			fileIncludePattern: '**/*.json',
			trendsLimit: 10,
			classifications: [
			    [
				'key': 'Browser',
				'value': 'Firefox'
			    ]
			]
	    }
    
    }
	configure { project ->
	  project / 'publishers' << 'net.masterthought.jenkins.CucumberReportPublisher' {
	    fileIncludePattern '**/*.json'
	    fileExcludePattern ''
	    jsonReportDirectory ''
	    failedStepsNumber '0'
	    skippedStepsNumber '0'
	    pendingStepsNumber '0'
	    undefinedStepsNumber '0'
	    failedScenariosNumber '0'
	    failedFeaturesNumber '0'
	    buildStatus 'FAILURE'  //other option is 'UNSTABLE' - if you'd like it left unchanged, don't provide a value
	    trendsLimit '0'
	    sortingMethod 'ALPHABETICAL'
	  }
}
}



