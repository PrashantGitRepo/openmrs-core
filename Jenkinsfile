pipeline {
  agent any
  stages {
    stage('Code Checkout') {
      steps {
<<<<<<< HEAD
        ws(dir: 'E:\\pipeline-workspace\\open-mrs') {
          git(url: 'https://github.com/PrashantGitRepo/openmrs-core.git', branch: 'master', poll: true)
        }

=======
        bat 'echo "...... Creating workspace ......"'
		bat 'mkdir -p E:\\pipeline-workspace\\open-mrs-2'
		bat 'echo "...... Cloning code into workspace ......"'
		bat	'git clone https://github.com/PrashantGitRepo/openmrs-core.git'
>>>>>>> 3ae9daf052057076e5e5ecb13fd0c6117c396fcc
      }
    }
    stage('Building Code') {
      steps {
            bat 'mvn clean compile package -DskipTests'
            fileExists 'openmrs.war'
      }
    }
    stage('Deploy war') {
      steps {
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