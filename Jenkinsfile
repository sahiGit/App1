pipeline {
    agent any
    stages {
        stage('Pull') {
            steps {
                git branch: 'Future1', url: 'https://github.com/sahiGit/App1.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    def myApp1 = docker.build("my-App-1")
                    sh 'docker build -t my-App-1 .'
                }
            }
        }
        stage('Push') {
            steps {
                sh 'docker login -u kubesamm -p sam@DockerHub'
                sh 'docker tag my-App-1 kubesamm/my-App-1'
                sh 'docker push kubesamm/my-App-1'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'kubectl apply -f K8/deployment.yaml'
                    sh 'kubectl set image deployment/my-App-1 my-App-1=kubesamm/my-App-1'
                }
            }
        }
    }
    post {
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
