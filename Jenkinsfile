pipeline {
    agent any

    environment {
        GIT_SSH_KEY = credentials('ssh-key') // Add your SSH credentials ID here
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    // Ensure the .ssh directory exists
                    sh 'mkdir -p $HOME/.ssh'
                    // Add GitHub to known_hosts
                    sh 'ssh-keyscan -H github.com >> $HOME/.ssh/known_hosts'
                }
                // Clone the repository using SSH
                git url: 'git@github.com:ai-insights-lab/jenkins_workshop.git', branch: 'main', credentialsId: 'ssh-key'
            }
        }

        stage('Configure Git') {
            steps {
                // Configure Git user email and name
                sh '''
                    git config --global user.email "insights.genai@gmail.com"
                    git config --global user.name "Dhiren"
                '''
            }
        }

        stage('Make Changes') {
            steps {
                script {
                    // Navigate to the repository directory
                    dir('jenkins_workshop') {
                        // Create a new file
                        sh 'echo "This is a new file" > newfile.txt'
                        // Add the file to the staging area
                        sh 'git add newfile.txt'
                        // Commit the file with a message
                        sh 'git commit -m "Add newfile.txt"'
                        // Push the commit to the remote repository
                        sh 'git push origin main'
                    }
                }
            }
        }
    }
}
