
pipeline{

    agent any

    stages {

        stage('Clean and Compile') { 
            steps {

                sh "mvn clean compile"
            }
        }
       
        stage('Junit5 Test') { 
            steps {

                sh "mvn test"
            }
        }
        
        stage('Maven Build') { 
            steps {
                sh "mvn package"
            }
        }

        stage ('Cucumber Reports') {

            steps {
                cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'

            }

        }

    }

}
