pipeline {
  agent any
  stages {
    stage('Code Checkout') {
      steps {
        ws(dir: 'E:\\pipeline-workspace\\open-mrs') {
          bat 'CD E:\\pipeline-workspace\\open-mrs'
          git(url: 'https://github.com/PrashantGitRepo/openmrs-core.git', branch: 'master', poll: true)
        }

      }
    }
    stage('Building Code') {
      steps {
		bat 'CD E:\\pipeline-workspace\\open-mrs'
        bat 'mvn clean compile package -DskipTests'
        fileExists 'openmrs.war'
      }
    }
    stage('Deploy war') {
      steps {
        bat 'CD E:\\pipeline-workspace\\open-mrs'
		bat 'COPY /Y E:\\pipeline-workspace\\open-mrs\\webapp\\target\\openmrs.war C:\\apache-tomcat-7.0.88\\webapps'
      }
    }
	stage('Start Tomcat Server') {
	  steps {
		bat 'CALL C:\\apache-tomcat-7.0.88\\bin\\startup.bat'
		bat 'PAUSE'
	  }
	}
  }
  environment {
    App_Dir = 'E:\\pipeline-workspace\\open-mrs\\'
  }
}