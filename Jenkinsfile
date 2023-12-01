def frontendImage="diehardgmb77/frontend"
def backendImage="diehardgmb77/backend"
def dockerRegistry=""
def registryCredentials="docker-hub"
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

	environment {
		PIP_BREAK_SYSTEM_PACKAGES = 1
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
				sh 'docker rm -f backend frontend || true'
			}
		}
		stage('deploy_application'){
			steps {
				script {
					withEnv(["FRONTEND_IMAGE=$frontendImage:$frontendDockerTag", 
						"BACKEND_IMAGE=$backendImage:$backendDockerTag"]) {
							docker.withRegistry("$dockerRegistry", "$registryCredentials") {
				                            sh "docker-compose up -d"
							}
						}
				}			
			}
		}
		stage('selenium_tests') {
			steps {
				sh 'pip3 install -r ./test/selenium/requirements.txt'
				sh 'python3 -m pytest ./test/selenium/frontendTest.py'
			}
		}
	}
    post {
        always {
          sh "docker-compose down"
          cleanWs()
        }
    }
}
