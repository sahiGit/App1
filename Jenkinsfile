pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building the project"'
                sh 'date'
                sh 'ls -al'
                sh 'mkdir mybuild'
                sh 'cd mybuild && pwd'
                // Add your additional build steps here
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests"'
                // Add your test steps here
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying the project"'
                // Add your deployment steps here
            }
        }
    }
    post {
        always {
            echo 'This will always run'
            // Add any necessary cleanup steps here
        }
        success {
            echo 'This will run only if the pipeline is successful'
            // Add actions to be performed if the pipeline succeeds
        }
        failure {
            echo 'This will run only if the pipeline fails'
            // Add actions to be performed if the pipeline fails
        }
    }
}
