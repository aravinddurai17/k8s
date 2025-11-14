pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/aravinddurai17/k8s.git'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f nginx-deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'kubectl get deployments'
                sh 'kubectl get pods -l app=nginx'
            }
        }
    }

    post {
        success {
            echo 'Nginx deployed successfully to k3d Kubernetes cluster!'
        }
    }
}
