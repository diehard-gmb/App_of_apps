def frontendImage="diehardgmb77/frontend"
def backendImage="diehardgmb77/backend"
def dockerRegistry=""
def registryCredentials="dockerhub"
def frontendDockerTag=""
def backendDockerTag=""


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
		stage('set_version'){
			steps {
				script {
					frontendDockerTag = params.frontendDockerTag.isEmpty() ? "latest" : params.frontendDockerTag
					backendDockerTag = params.backendDockerTag.isEmpty() ? "latest" : params.backendDockerTag
				}
			}
		}
		stage('remove_containers') {
			steps {
				sh 'ls -ltra'
			}
		}
	}
}
