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
		}
		}
        }
	
        stage('Deploy') {
            steps {
                sh 'mvn package'
            }
        }

	stage('cat README'){
	when{
	 branch "bug*"
	}
        steps{
		sh 'cat README.md'
	}
	}

        stage('Archiving') {
            steps {
                archiveArtifacts '**/target/*.jar'
            }
        }
    }
}
