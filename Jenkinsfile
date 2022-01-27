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
                    docker run --rm 
                    -v //c/tmp/flyway:/flyway/sql 
                    flyway/flyway 
                    -url=jdbc:postgresql://192.168.2.140:5431/postgres 
                    -schemas=flyway_test 
                    -user=dbuser 
                    -password=dbuser_password 
                    migrate
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