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
        script {
            sh 'echo $SSH_KEY'
            sh 'cat $SSH_KEY'
            sh 'sshpass -p ubuntu scp -o StrictHostKeyChecking=no -i $SSH_KEY target/gamutkart.war ubuntu@172.31.44.59:/var/lib/tomcat9/webapps/'
        }
    }
}
}   
