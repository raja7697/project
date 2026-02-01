pipeline {
    agent any

    tools {
        // Name must match the Maven installation configured in Jenkins
        maven 'Maven-3.9.6'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/your-org/your-repo.git'
            }
        }

        stage('clean-repo') {
            steps {
                sh '''
                    rm -rf ~/.m2/repository/*
                    rm -rf /mnt/servers/apache-tomcat-10.1.48/webapps/LoginWebApp*
                '''
            }
        }

        stage('clean-mvn-package') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('deploy') {
            steps {
                sh 'cp target/LoginWebApp.war /mnt/servers/apache-tomcat-10.1.49/webapps/'
            }
        }
    }
}
