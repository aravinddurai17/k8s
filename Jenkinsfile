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
                sh 'kubectl apply -f nginx-deployment.yaml --validate=false --insecure-skip-tls-verify'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'kubectl get deployments'
                sh 'kubectl get pods --insecure-skip-tls-verify'
            }
        }
    }

    post {
        success {
            echo 'Nginx deployed successfully to k3d Kubernetes cluster!'
        }
    }
}
