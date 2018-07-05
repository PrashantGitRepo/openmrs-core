pipeline {
  agent any
  stages {
    stage('Code Checkout') {
      steps {
        bat 'echo "...... Creating workspace ......"'
		bat 'mkdir -p E:\\pipeline-workspace\\open-mrs'
		bat 'echo "...... Cloning code into workspace ......"'
		scm	'git config --global user.email 'prashant.0542@gmail.com''
		scm	'git config --global user.name 'vickyru''
		scm	'git config --global push.default simple'
		scm	'git clone https://github.com/PrashantGitRepo/openmrs-core.git'
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