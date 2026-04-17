pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/vipultalele-04/k8s-Assignment.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f .'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
