pipeline { 
    agent any 
    stages {
        stage('compile and clean') { 
            steps { 
                echo 'HELLO MULTIBRANCH'
		sh 'mvn clean compile'
            }
        }
          stage('Test'){
            steps {
                sh 'mvn test site'
            }
		post{
		always{
			junit allowEmptyResults:true, testResults:'target/surefire-reports/*.xml'
			 publishHTML target: [
             			 allowMissing: false,
             			 alwaysLinkToLastBuild: false,
             			 keepAll: true,
              			 reportDir: 'coverage',
             			 reportFiles: 'index.html',
             			 reportName: 'JUnit Test Report'
            		]
		}
		}
        }
     stage('Deploy') {
            steps {
                sh 'mvn package'
            }
        }
stage('Archiving') {
        steps {
                archiveArtifacts '**/target/*.jar'
            }
        }
    }
}
