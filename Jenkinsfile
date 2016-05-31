docker.image('cloudbees/java-build-tools:0.0.6').inside {

   // Mark the code checkout 'stage'....
   stage 'Checkout'

   // Get some code from a GitHub repository
   checkout scm

   // Mark the code build 'stage'....
   stage 'Build'
   // Run the maven build
   sh "mvn -B clean verify -Dmaven.test.failure.ignore=true"

   stage 'Report'
   step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/*.xml'])
}
