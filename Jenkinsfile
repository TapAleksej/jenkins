pipeline {	
	agent any
	parameters {
		choice(name: 'ENVIRONMENT', choices: ['dev', 'stage', 'prod'], description: 'Target environment')
		booleanParam(name: 'RUN_TEST', defaultValue: true, description: 'Run test?' )
		string(name: 'VERSION', defaultValue: 'latest')
		string(name: 'PASSWD', defaultValue: 'secret', description: 'Enter password')
	}
	
	stages {
		stage('Init') {
			steps {
				echo "Deploy ${params.VERSION} to ${params.ENVIRONMENT}"
				script {
					currentBuild.displayName = "#${BUILD_NUMBER}-${params.ENVIRONMENT}" 
				}
			}		
		}
		
		stage('Run tests') {
			when {
				expression { params.RUN_TEST == true}
			}
			steps {
				echo "Login into QA (test or staged) system with ${params.PASSWD}"
			}
		}	
	}
}
