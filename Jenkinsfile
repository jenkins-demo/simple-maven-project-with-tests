node {
   stage ('Checkout') {
      // Get some code from a GitHub repository
      checkout scm
   }
   
   stage ('Build') {
      // Get the maven tool.
      // ** NOTE: This 'M3' maven tool must be configured
      // **       in the global configuration.           
      def mvnHome = tool 'M3'

      // Run the maven build
      sh "${mvnHome}/bin/mvn -B clean verify -Dmaven.test.failure.ignore=true"
   }
   
   stage ('Report') {
      step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/*.xml'])
   }
}
