pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
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
                sh '/home/kunalshiwarkar/Documents/Devops_software/tar/apache-maven-3.9.7/bin/mvn install'
            }
        }
        stage('Deployment') {
            steps {
                script {
                    if (env.ENVIRONMENT == 'QA') {
                        sh 'cp target/cicd.war /home/kunalshiwarkar/Documents/Devops_software/tar/apache-tomcat-9.0.89/webapps'
                        echo "deployment has been done on QA!"
                    } else if (env.ENVIRONMENT == 'UAT') {
                        sh 'cp target/cicd.war /home/kunalshiwarkar/Documents/Devops_software/tar/apache-tomcat-9.0.89/webapps'
                        echo "deployment has been done on UAT!"
                    }
                    echo "deployment has been done!"
                }
            }
        }
    }
}
