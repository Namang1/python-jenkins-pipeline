pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Namang1/python-jenkins-pipeline.git'
            }
        }

        stage('Check Poetry') {
            steps {
                sh '''
                if ! command -v poetry &> /dev/null
                then
                    echo "Poetry not found!"
                    exit 1
                fi
                poetry --version
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'poetry install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'echo "No tests defined."'
            }
        }

        stage('Restart FastAPI Service') {
            steps {
                sh 'sudo systemctl restart fastapi-jenkins.service'
            }
        }
    }
}




// ## sudo nano /etc/systemd/system/fastapi-jenkins.service
// ## write the systemd file here with all the necessary things
// #commands to activate the service
// sudo systemctl daemon-reexec
// sudo systemctl daemon-reload
// sudo systemctl enable fastapi-jenkins.service
// sudo systemctl start fastapi-jenkins.service

