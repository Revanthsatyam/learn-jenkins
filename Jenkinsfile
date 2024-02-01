pipeline {
    //agent any
    agent { node { label 'workstation' } }

    environment {
      TEST_URL = "google.com"
    }

    stages {
      stage('Compile') {
        steps {
          //echo 'Hello World'
          //error 'This is an error'
          echo TEST_URL
        }
      }
    }

    post {
      always{
        echo 'post'
        // Send Email
        // Trigger Some another job
        // Update Some JIRA status about the build
      }
    }
}
