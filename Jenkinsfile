pipeline {
	agent any
	tools {
		maven 'maven 3.9.9'
	}

	parameters {
		choice(name: 'DEPLOY_ENVIRONMENT', choices: ['tomcat1', 'tomcat2'], description: 'Ambiente de despliegue')
	}

	stages {
		stage('PackageDocker') {
			steps {
				//bat "echo hola"
				bat 'mvn -B -q -P docker-build clean package'
			}
		}
		/*
		stage('Deploy') {
			steps {
				bat 'docker build -t ' + params.DEPLOY_ENVIRONMENT + ' .'
				bat 'cd ' + env.ENVS_DIR + ' && docker compose down ' + params.DEPLOY_ENVIRONMENT + ' && docker compose up -d ' + params.DEPLOY_ENVIRONMENT
			}
		}
  		*/
	}
}
