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
                    wget -qO- https://repo1.maven.org/maven2/org/flywaydb/flyway-commandline/8.4.3/flyway-commandline-8.4.3-linux-x64.tar.gz | tar xvz && sudo ln -s `pwd`/flyway-8.4.3/flyway /usr/local/bin 
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