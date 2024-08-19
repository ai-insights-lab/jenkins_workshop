pipeline {
    agent any

    stages {
        stage('Development') {
            steps {
                echo 'Hello World - Development'
                bat 'git clone https://github.com/ai-insights-lab/jenkins_workshop.git'
            }
        }
        stage('QA') {
            steps {
                echo 'Hello World - QA'
            }
        }
        stage('UAT') {
            steps {
                echo 'Hello World - UAT'
            }
        }
        stage('Pre-Prod') {
            steps {
                echo 'Hello World - Pre-Prod'
            }
        }
    }
}
