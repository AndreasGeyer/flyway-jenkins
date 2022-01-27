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
            when {branch "main"}
            steps {
                echo "I am a master branch"
            }
            when {branch "test"}
            steps {
                echo "I am a Test branch"
            }
        }
    }
}