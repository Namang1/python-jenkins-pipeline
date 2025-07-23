pipeline {
    agent any

    environment {
        PATH = "/var/lib/jenkins/.local/bin:$PATH"  // add Poetry's path to environment
    }

    stages {
        stage('Check Poetry') {
            steps {
                sh '''
                    if ! command -v poetry &> /dev/null; then
                      echo "❌ Poetry not found! Exiting."
                      exit 1
                    fi
                    echo "✅ Poetry found:"
                    poetry --version
                '''
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'poetry install'
            }
        }

        stage('Run Server') {
            steps {
                sh 'poetry run uvicorn app.main:app --host 0.0.0.0 --port 8000 &'
            }
        }
    }
}
