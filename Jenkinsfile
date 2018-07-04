pipeline {
  agent any
  stages {
    stage('Code Checkout') {
      steps {
        ws(dir: 'E:\\pipeline-workspace\\open-mrs') {
          bat 'CD E:\\pipeline-workspace\\open-mrs'
          git(url: 'https://github.com/PrashantGitRepo/openmrs-core.git', branch: 'master')
        }

      }
    }
    stage('Building Code') {
      steps {
        bat(script: 'CD E:\\pipeline-workspace\\open-mrs', returnStatus: true)
        bat 'mvn clean compile package -DskipTests'
        fileExists 'openmrs.war'
      }
    }
    stage('Cleanup') {
      steps {
        cleanWs(cleanWhenSuccess: true)
      }
    }
  }
  environment {
    App_Dir = 'E:\\pipeline-workspace\\open-mrs\\'
  }
}