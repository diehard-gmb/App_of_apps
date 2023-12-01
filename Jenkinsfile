def frontendImage="pandaacademy/frontend"
def backendImage="pandaacademy/backend"
def dockerRegistry=""
def registryCredentials="dockerhub"

pipeline {

	agent {
		label 'master'
	}
	
	stages {
		stage('get_code'){
			steps {

				checkout scm

			}
		}
	}
}
