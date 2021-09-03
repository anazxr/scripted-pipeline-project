node {
    stage('Build') {
        echo 'Running build automation'
        sh './gradlew build --no-daemon'
        archiveArtifacts artifacts: 'dist/app.zip'
    }
    stage('Unit & Integration Tests') {
        script {
              try {
                sh './gradlew clean test --no-daemon' //run a gradle task
                  } finally {
                        junit '**/build/test-results/test/*.xml' //make the junit test results available in any case (success & failure)
                    }
               }
         }
    stage('Archive') {
		archive 'ProjectName/bin/Release/**'
    }
 }
