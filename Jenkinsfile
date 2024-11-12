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
				//bat 'mvn clean install -U'
				bat 'mvn -B -q -P docker-build clean package'
				//bat 'mvn -B -q package'
			}
		}

		stage('Deploy') {
			when {
				not {
					equals expected: 'ninguno', actual: params.DEPLOY_ENVIRONMENT
				}
			}
			steps {
				//bat 'D:\\devenv\\JENKINS_CURSO\\AMBIENTES\\tomcat1\\bin\\shutdown.bat'
				bat 'copy target\\ROOT.war D:\\devenv\\JENKINS_CURSO\\AMBIENTES\\' + params.DEPLOY_ENVIRONMENT + '\\webapps'
				//bat 'D:\\devenv\\JENKINS_CURSO\\AMBIENTES\\tomcat1\\bin\\startup.bat'
			}
		}
	}
}
