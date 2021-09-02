node {
    stage ('Build') {
        echo 'Running build automation'
        sh './gradlew.bat build --no-daemon'
        archiveArtifacts artifacts: 'dist/app.zip'
     }
     stage('Test') {
        script {
                    try {
                        sh './gradlew clean test --no-daemon' //run a gradle task
                    } finally {
                        junit '**/build/test-results/test/*.xml' //make the junit test results available in any case (success & failure)
                    }
                }
           }
