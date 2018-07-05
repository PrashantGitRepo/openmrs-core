pipeline {
  agent any
  stages {
    stage('Code Checkout') {
      steps {
        ws(dir: 'E:\\pipeline-workspace\\open-mrs') {
          git(url: 'https://github.com/PrashantGitRepo/openmrs-core.git', branch: 'master', poll: true)
        }
		bat 'echo "...... Creating workspace ......"'
		bat 'mkdir -p E:\\pipeline-workspace\\open-mrs'
		bat 'echo "...... Cloning code into workspace ......"'
		bat	'git config --global user.email 'email@address.com' &&
			git config --global user.name 'myname' &&
			git config --global push.default simple'

      }
    }
    stage('Building Code') {
      steps {
		bat 'CD E:\\pipeline-workspace\\open-mrs && mvn clean compile package -DskipTests'
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
		bat 'C:\\apache-tomcat-7.0.88\\bin\\catalina.bat stop'
		bat 'C:\\apache-tomcat-7.0.88\\bin\\catalina.bat start'
	  }
	}
  }
  environment {
    App_Dir = 'E:\\pipeline-workspace\\open-mrs\\'
  }
}