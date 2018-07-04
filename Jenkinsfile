pipeline {
  agent any
  stages {
    stage('Code Checkout') {
      steps {
        ws(dir: 'E:\\pipeline-workspace\\open-mrs') {
          git(url: 'https://github.com/PrashantGitRepo/openmrs-core.git', branch: 'master')
        }

      }
    }
    stage('Building Code') {
      steps {
        bat 'E:\\pipeline-workspace\\open-mrs'
        bat 'mvn clean compile package -DskipTests'
        fileExists 'openmrs.war'
      }
    }
  }
  environment {
    App_Dir = 'E:\\pipeline-workspace\\open-mrs\\'
  }
}