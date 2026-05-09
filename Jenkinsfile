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
        // Using the * wildcard to match any version of the war file
        sh 'cp target/MyMavenWebApp01*.war /opt/tomcat/webapps/MyMavenWebApp01.war'
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
