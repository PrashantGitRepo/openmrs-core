pipeline {
  agent any
  stages {
    stage('Code Checkout') {
      steps {
        ws(dir: 'E:\\pipeline-workspace\\open-mrs') {
          git(url: 'https://github.com/PrashantGitRepo/openmrs-core.git', changelog: true, branch: 'master', poll: true)
        }

      }
    }
    stage('Build The Code') {
      steps {
        dir(path: 'E:\\pipeline-workspace\\open-mrs') {
          bat 'mvn clean compile package -DskipTests'
          fileExists 'openmrs.war'
        }

      }
    }
  }
}