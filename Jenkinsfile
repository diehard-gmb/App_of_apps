def frontendImage="diehardgmb77/frontend"
def backendImage="diehardgmb77/backend"
def dockerRegistry=""
def registryCredentials="dockerhub"

pipeline {

	agent {
		label 'master'
	}

    	parameters {
        	string(name: 'backendDockerTag', defaultValue: '', description: 'Backend tag')
	        string(name: 'frontendDockerTag', defaultValue: '', description: 'Frontend tag')
	}	
	
	stages {
		stage('get_code'){
			steps {

				checkout scm

			}
		}
	}
}
