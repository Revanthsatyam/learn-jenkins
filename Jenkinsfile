// pipeline {
//  //agent any
//  agent { node { label 'workstation' } }
//
//  environment {
//    TEST_URL = "google.com"
//    SSH = credentials("centos-ssh")
//  }
//
//  options {
//    ansiColor('xterm')
//  }
//
//  parameters {
//    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
//
//    text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
//
//    booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
//
//    choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
//
//    password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
//  }
//  triggers { pollSCM('*/1 * * * *') }
//
//  tools {
//    maven 'maven'
//  }
//
//  stages {
//
//    stage('Compile') {
// //      input {
// //        message "Should we continue?"
// //        ok "Yes, we should."
// //      }
//
//      when {
//        branch 'production'
//      }
//      steps {
//        //echo 'Hello World'
//        //error 'This is an error'
//        echo TEST_URL
//        echo SSH
//        sh 'env'
//        sh 'ansible -i 172.31.85.208, all -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -m ping'
//        sh 'mvn version'
//      }
//    }
//
//  }
//
//  post {
//    always {
//      echo 'Post'
//      // Send Email
//      // Trigger Some another Job
//      // Update some JIRA Status about the build.
//    }
//  }
//
// }


//pipeline {
//  agent any
//  stages {
//    stage('Non-Parallel Stage') {
//      steps {
//        echo 'This stage will be executed first.'
//      }
//    }
//    stage('Parallel Stage') {
//      failFast true
//      parallel {
//        stage('Branch A') {
//          agent {
//            label "for-branch-a"
//          }
//          steps {
//            echo "On Branch A"
//          }
//        }
//        stage('Branch B') {
//          agent {
//            label "for-branch-b"
//          }
//          steps {
//            echo "On Branch B"
//          }
//        }
//        stage('Branch C') {
//          agent {
//            label "for-branch-c"
//          }
//          stages {
//            stage('Nested 1') {
//              steps {
//                echo "In stage Nested 1 within Branch C"
//              }
//            }
//            stage('Nested 2') {
//              steps {
//                echo "In stage Nested 2 within Branch C"
//              }
//            }
//          }
//        }
//      }
//    }
//  }
//}

// def x = 10
// env.y = 20 // When you need to access a variable inside a shell then declare the variable like this otherwise you can declare like above.
// def samplef() {
//   print "XYZ Function"
// }
//
// node('workstation') {
//   if (x >10 ) {
//     stage('Test') {
//       print x
//       sh 'echo y - ${y}' // You can access the variables like this.
//       samplef()
//     }
//   } else {
//     stage('Test1') {
//       samplef()
//     }
//   }
//
// }

pipeline {
 agent any
//  agent { node { label 'workstation' } }

 environment {
   TEST_URL = "google.com"
   SSH = credentials("centos-ssh")
 }

//  options {
//    ansiColor('xterm')
//  }

 parameters {
   string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

   text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

   booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

   choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

   password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
 }
 triggers { pollSCM('*/1 * * * *') }

 tools {
   maven 'maven'
 }

 stages {

   stage('Compile') {
//      input {
//        message "Should we continue?"
//        ok "Yes, we should."
//      }

     when {
       branch 'main'
     }
     steps {
       //echo 'Hello World'
       //error 'This is an error'
       echo TEST_URL
       echo SSH
       sh 'env'
       sh 'ansible -i 172.31.85.208, all -e ansible_user=${SSH_USR} -e ansible_password=${SSH_PSW} -m ping'
       sh 'mvn version'
     }
   }

 }

 post {
   always {
     echo 'Post'
     // Send Email
     // Trigger Some another Job
     // Update some JIRA Status about the build.
   }
 }

}