pipeline {
    //agent any
    agent { node { label 'workstation' } }

    environment {
      TEST_URL = "google.com"
      SSH = credentials("centos-ssh")
    }

    stages {
      stage('Compile') {
        steps {
          //echo 'Hello World'
          //error 'This is an error'
          echo TEST_URL
          echo SSH
          sh 'env'
          sh 'ansible -i 172.31.28.60, all -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -m ping'
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
