pipeline {
  agent any
  stages {
    stage('Code Checkout') {
      steps {
        ws(dir: '%App_Dir%') {
          git(url: 'https://github.com/PrashantGitRepo/openmrs-core.git', branch: 'master')
        }

      }
    }
    stage('Building Code') {
      steps {
        bat 'cd %App_Dir%'
        bat 'mvn clean compile package -DskipTests'
        fileExists 'openmrs.war'
      }
    }
  }
  environment {
    App_Dir = 'E:\\pipeline-workspace\\open-mrs\\'
  }
}