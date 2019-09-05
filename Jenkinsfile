pipeline {
	agent {label 'maven'}
	stages {
		stage('git clone') {
			steps {
				script {
					git url:'https://github.com/shadow700317/aztl-demo-zh.git',branch:'master'
				}
			}
		}
		stage('mvn') {
			steps {
				echo "building...."
				sh 'mvn clean package'
				//archiveArtifacts artifacts: '**/target/*.jar', fingerprint : true
				echo "build finish"
			}
		}
		stage('Test') {
			steps {
				echo "testing..."
				sh 'mvn test'
				echo 'test finish'
				junit '**/target/surefire-reports/*.xml'
			}
		}
		stage('confirm') {
			steps {
				input message: 'deploy',
				ok:'yes'
			}
		}
	}

}
