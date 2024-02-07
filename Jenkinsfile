pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }
	 stage ('Build'){
	        steps {
			sh 'mvn clean install'
                }
	}

	stage('Run Tests') {
	    steps {
	       sh 'mvn test'
	    }
	}

        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	stage('Deployment') {
	   steps {
		sh 'sshpass -p ubuntu scp target/gamutkart.war ubuntu@172.31.44.59:/var/lib/tomcat9/webapps/'
	}
    }
}
}
