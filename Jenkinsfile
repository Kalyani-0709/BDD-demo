pipeline{

    agent any

    stages {

        stage ('Compile Stage') {

            steps {
               
                    bat 'mvn compile'                

            }
        }
        
    	stage ('Test Stage') {

            steps {
                
                    bat 'mvn test'
                

            }
        }       
        
		stage ('Build Stage') {

            steps {
               
                    bat 'mvn package'                

            }
        }

	    stage('testing pipeline'){
		  steps{
	      echo 'test1'
			sh 'mkdir from-jenkins'
			sh 'touch from-jenkins/test.txt'
			}
		}
        stage ('Cucumber Reports') {

            steps {
                 cucumber buildStatus: 'UNSTABLE',
                reportTitle: 'My report',
                fileIncludePattern: '**/*.json',

            }

        }
        

    }
	node () {
	   stage ('blah') {
		def get_current_time_date = {
		    return 'hoge'
		}

		echo get_current_time_date()
	    }
}

}
