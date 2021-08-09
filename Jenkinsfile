
post {
    always {
        cucumber buildStatus: 'UNSTABLE',
                failedFeaturesNumber: 1,
                failedScenariosNumber: 1,
                skippedStepsNumber: 1,
                failedStepsNumber: 1,
                classifications: [
                        [key: 'Commit', value: '<a href="${GERRIT_CHANGE_URL}">${GERRIT_PATCHSET_REVISION}</a>'],
                        [key: 'Submitter', value: '${GERRIT_PATCHSET_UPLOADER_NAME}']
                ],
                reportTitle: 'My report',
                fileIncludePattern: '**/*cucumber-report.json',
                sortingMethod: 'ALPHABETICAL',
                trendsLimit: 100
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
