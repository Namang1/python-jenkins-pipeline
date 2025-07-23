pipeline {
    agent any

    environment {
        PATH = "${env.HOME}/.local/bin:${env.PATH}"  
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Verify Poetry Installation') {
            steps {
                sh 'poetry --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'poetry install'
            }
        }

        stage('Run App with Uvicorn') {
            steps {
                sh 'poetry run uvicorn main:app --host 0.0.0.0 --port 8010 --workers 2 &'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution complete.'
        }
    }
}
