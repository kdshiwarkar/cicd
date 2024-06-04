pipeline {
	agent any
	
	parameters {
		choice(name: 'ENVIRONMENT', choices: ['QA','UAT'], description: 'Pick Environment value')
	}
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }
	    }
		stage('Build') {
	           steps {
			  sh 'mvn install'
	                 }
		}
		stage('Deployment'){
		    steps {
			script {
			 if ( env.ENVIRONMENT == 'QA' ){
        	sh 'cp target/cicd.war /home/kunalshiwarkar/Documents/Devops_software/tar/apache-tomcat-9.0.89/webapps/'
        	echo "deployment has been done on QA!"
			 }
			elseif ( env.ENVIRONMENT == 'UAT' ){
    		sh 'cp target/cicd.war /home/kunalshiwarkar/Documents/Devops_software/tar/apache-tomcat-9.0.89/webapps'
    		echo "deployment has been done on UAT!"
			}
			echo "deployment has been done!"
			fi
				
			}
		    }
		}	
	}
}
