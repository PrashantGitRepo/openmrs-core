pipeline {
  agent any
  stages {
    stage('Code Checkout') {
      parallel {
        stage('Code Checkout') {
          steps {
            ws(dir: 'E:\\pipeline-workspace\\') {
              git(url: 'https://github.com/PrashantGitRepo/openmrs-core.git', branch: 'master')
            }

          }
        }
        stage('Verify The Workspace') {
          steps {
            fileExists 'pom.xml'
          }
        }
      }
    }
    stage('Build The Code') {
      steps {
        dir(path: 'E:\\pipeline-workspace\\openmrs-core\\') {
          bat 'mvn clean compile package -DskipTests'
          fileExists 'openmrs.war'
        }

      }
    }
  }
}