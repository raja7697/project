pipeline {
    agent any

 

    stages {

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
