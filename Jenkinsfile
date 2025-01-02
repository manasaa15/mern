pipeline {
    agent any
    tools {
        nodejs '20.11.0' // Node.js tool name configured in Jenkins
    }
    environment {
        SONAR_SCANNER_HOME = 'C:\\Users\\Admin\\Downloads\\scanner\\sonar-scanner-6.2.1.4610-windows-x64\bin'
        SONAR_HOST_URL = 'http://localhost:9000'
        SONAR_PROJECT_KEY = 'backend_task'
        SONAR_PROJECT_NAME = 'backend_task'
        SONAR_TOKEN = 'sqp_a3d05eb002e43a7f4e04987fb5ba80850b952c36'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/manasaa15/mern.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                bat """
                "C:\\Users\\Admin\\Downloads\\scanner\\sonar-scanner-6.2.1.4610-windows-x64\\binsonar-scanner.bat" ^
                -D"sonar.projectKey=backend-task" ^
                -D"sonar.sources=." ^
                -D"sonar.host.url=http://localhost:9000" ^
                -D"sonar.token=sqp_a3d05eb002e43a7f4e04987fb5ba80850b952c36"
                """
              
        }
    }
    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            echo 'SonarQube analysis completed successfully!'
        }
    }
}