pipeline {
    agent any
    stages {
        stage('Setup') {
            steps {
                sh 'echo "Begin Pulling changes"'
                sh '''
                    echo 'Pulling...' + env.BRANCH_NAME
                '''
            }
        }
        stage('Main Branch'){
            when {branch "main"}
            steps {
                echo "I am a master branch"
            }
        }
        stage('Test Branch'){
            when {branch "test"}
            steps {
                echo "I am a Test branch"
            }
        }
        stage('Jenkins Branch'){
            when {branch "Jenkinsfile"}
            steps {
                echo "I am a Test branch"
            }
        }
    }
}