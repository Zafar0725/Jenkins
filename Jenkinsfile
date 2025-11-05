pipeline {
  agent any

  // Use webhook (recommended). In the Jenkins job, tick:
  // "GitHub hook trigger for GITScm polling"
  triggers { githubPush() }

  options { timestamps() }

  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM',
          branches: [[name: '*/main']],
          userRemoteConfigs: [[
            url: 'https://github.com/Zafar0725/Jenkins.git',
            credentialsId: 'github-pat' // create this in Jenkins
          ]]
        ])
      }
    }

    stage('Build') {
      steps {
        echo 'Simulating build...'
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
        echo 'Running tests...'
        script {
          if (isUnix()) {
            sh 'echo "All tests passed (simulated)"'
          } else {
            bat 'echo All tests passed (simulated)'
          }
        }
      }
    }
  }

  post {
    success { echo '✅ SUCCESS — notifying team (console)' }
    failure { echo '❌ FAILED — notifying team (console)' }
    always  { echo "Build complete for commit: ${env.GIT_COMMIT ?: 'N/A'}" }
  }
}
