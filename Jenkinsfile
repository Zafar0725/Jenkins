pipeline {
  agent any

  /* Polling trigger (every ~5 min) */
  triggers { pollSCM('H/5 * * * *') }

  options { timestamps() }

  environment {
    EMAIL_TO = 'you@gmail.com'   // <-- change to your email
  }

  stages {
    stage('Checkout') {
      steps {
        echo '--- CHECKOUT ---'
        git branch: 'main', url: 'https://github.com/Zafar0725/Jenkins.git'
      }
    }

    stage('Build') {
      steps {
        echo '--- BUILD ---'
        script {
          if (isUnix()) {
            sh 'echo "Build step: compiling (simulated)"'
          } else {
            bat 'echo Build step: compiling (simulated)'
          }
        }
      }
    }

    stage('Test') {
      steps {
        echo '--- TEST ---'
        script {
          if (isUnix()) {
            sh 'echo "Running tests... All tests passed (simulated)"'
          } else {
            bat 'echo Running tests... All tests passed (simulated)'
          }
        }
      }
    }
  }

  /* Notifications */
  post {
    success {
      echo '✅ SUCCESS — notifying team by email'
      emailext(
        to: env.EMAIL_TO,
        subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
        body: """Build Succeeded.

Job: ${env.JOB_NAME}
Build: #${env.BUILD_NUMBER}
Branch: ${env.BRANCH_NAME ?: 'main'}
URL: ${env.BUILD_URL}console
"""
      )
    }
    failure {
      echo '❌ FAILURE — notifying team by email'
      emailext(
        to: env.EMAIL_TO,
        subject: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
        body: """Build Failed.

Job: ${env.JOB_NAME}
Build: #${env.BUILD_NUMBER}
Branch: ${env.BRANCH_NAME ?: 'main'}
URL (console): ${env.BUILD_URL}console
"""
      )
    }
    always {
      echo "Build complete for commit: ${env.GIT_COMMIT ?: 'N/A'}"
    }
  }
}
