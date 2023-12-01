def frontendImage="diehardgmb77/frontend"
def backendImage="diehardgmb77/backend"
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
