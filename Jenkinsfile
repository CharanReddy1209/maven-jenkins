pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/CharanReddy1209/maven-jenkins.git'
            }
        }
        stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('deploy') {
            steps {
                deploy adapters : [
                    tomcat9(
                        credentialsId: 'fe476ba2-c67b-43be-b941-45b6814fe275',
                        path: '',
                        url: 'http://174.138.33.98:8085/'
                        )
                    ],
                    contextPath: 'netflix',
                    war: 'target/*.war'
                
            }
        }
    }
}
