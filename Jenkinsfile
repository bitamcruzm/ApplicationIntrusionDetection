pipeline {
    agent any

	environment {
        env.PATH = "${tool 'Maven 3.3.9'}/bin:${env.PATH}"
	}

    stages {
		stage('Clone') {
			steps {
				git 'https://github.com/dschadow/ApplicationIntrusionDetection.git'
			}
		}

		stage('Version') {
			steps {
				sh 'mvn versions:set'
			}
		}

		stage('Build') {
			steps {
				sh 'mvn clean package'
			}
		}

		stage('Archive') {
			steps {
				junit allowEmptyResults: true, testResults: '**/target/**TEST*.xml'
			}
		}
	}
}