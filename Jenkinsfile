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
        stage('Apply Changes on Test'){
            when {branch "Jenkinsfile"}
           
            steps {
                sh """
                    flyway info
                    """
            }
        }
        stage('Jenkins Branch'){
            when {branch "Jenkinsfile"}
            steps {
                echo "I am a Jenkinsfile branch"
            }
        }
    }
}