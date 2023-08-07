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
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'mvn package'
            }
        }
<<<<<<< HEAD
	stage('cat README'){
	when{
	 branch "bug*"
	}
        steps{
		sh 'cat README.md'
	}
	}

=======
        
        stage('Archiving') {
            steps {
                archiveArtifacts '**/target/*.jar'
            }
        }
>>>>>>> 2efd2f04ba3d5a95d227e951ba43502c9278fe53
    }
}
