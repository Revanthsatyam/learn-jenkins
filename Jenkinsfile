pipeline {
    //agent any
    agent { node { label 'workstation' } }

    environment {
      TEST_URL = "google.com"
      SSH = credentials("centos-ssh")
    }

    options {
      ansiColor('xterm')
    }

    parameters {
      string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

      text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

      booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

      choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

      password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
//I have added a comment here
    triggers { pollSCM('*/1 * * * *') }

    tools {
      maven 'maven'
    }

    stages {
      stage('Compile') {
//         input {
//           message "Should we continue?"
//           ok "Yes, we should."
//         }
        when {
          branch 'production'
        }
        steps {
          //echo 'Hello World'
          //error 'This is an error'
          echo TEST_URL
          echo SSH
          sh 'env'
          sh 'ansible -i 172.31.28.60, all -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -m ping'
          sh 'mvn version'
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
