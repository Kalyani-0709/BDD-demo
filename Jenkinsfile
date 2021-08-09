pipeline {


  environment {
    //Project Configurations
    solutionName="bdd-atm"
    reportUrl = "http://ec2-54-90-56-187.compute-1.amazonaws.com:8080//job/$env.JOB_NAME/$env.BUILD_NUMBER/cucumber-html-reports/overview-failures.html"


  }

  agent any

  stages {
       
   stage('Run Tests') {
       steps {

            script {
              echo "Starting ${params.test} on ${params.environment} environment ${params.platform} platform with ${params.browser} browser"
              sh """docker run -v ${env.WORKSPACE}:/${solutionName} ${solutionName}:${env.BUILD_NUMBER} cucumber features/${params.test}/${params.feature}.feature -p ${params.environment} -p ${params.platform} -p ${params.browser} -p ${params.report}"""
             }

       }
   }

  }

  post {
  	     failure {

  	      echo "Test failed"
                      cucumber buildStatus: 'FAIL',
                                   failedFeaturesNumber: 1,
                                   failedScenariosNumber: 1,
                                   skippedStepsNumber: 1,
                                   failedStepsNumber: 1,
                                   fileIncludePattern: '**/*.json',
                                   sortingMethod: 'ALPHABETICAL'

          slackSend color: 'red', message: "${params.reportname} Tests failed. >> Click to view <$reportUrl|report>"

  	     }

  	      success {

          echo "Test succeeded"
                     cucumber buildStatus: 'SUCCESS',
                                            failedFeaturesNumber: 0,
                                            failedScenariosNumber: 0,
                                            skippedStepsNumber: 0,
                                            failedStepsNumber: 0,
                                            fileIncludePattern: '**/*.json',
                                            sortingMethod: 'ALPHABETICAL'

          slackSend color: 'green', message: "${params.reportname} Tests passed. >> Click to view <$reportUrl|report>"

          }

  }

}
