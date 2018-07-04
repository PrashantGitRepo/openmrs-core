pipeline {
  agent any
  stages {
    stage('Code Checkout') {
      steps {
        ws(dir: '$App_Dir;/open-mrs') {
          git(url: 'https://github.com/PrashantGitRepo/openmrs-core.git', changelog: true, branch: 'master')
        }

      }
    }
    stage('Build The Code') {
      steps {
        dir(path: 'E:\\pipeline-workspace\\') {
          bat 'mvn clean compile package -DskipTests'
          fileExists 'openmrs.war'
        }

      }
    }
  }
  environment {
    App_Dir = 'E:\\pipeline-workspace'
  }
}