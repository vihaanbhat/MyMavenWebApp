pipeline {
    agent any 

    tools {
        // Ensure 'Maven' matches the name in Manage Jenkins > Tools
        maven 'Maven' 
    }

    stages {
        stage('Checkout') {
            steps {
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
                // Using the specific artifact and version you provided
                sh 'cp target/MyMavenApp-1.0-SNAPSHOT.war /opt/tomcat/webapps/MyMavenApp.war'
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
