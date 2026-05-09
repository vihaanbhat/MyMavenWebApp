pipeline {
    agent any 

    tools {
        maven 'Maven' 
    }

    stages {
        stage('Checkout') {
            steps {
                // Changed 'master' to 'main' to match your repository settings
                git branch: 'main', url: 'https://github.com/vihaanbhat/MyMavenWebApp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package' 
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test' 
            }
        }

        stage('Deploy WAR') {
            steps {
                sh 'cp target/MymavenWebApp01.war /opt/tomcat/webapps/'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
