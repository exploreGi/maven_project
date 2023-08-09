pipeline { 
    agent any 
    stages {
        stage('compile and clean') { 
            steps { 
                sh 'printenv'
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
