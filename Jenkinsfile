pipeline {
    agent any

    environment {
        POETRY_HOME = "/var/lib/jenkins/.local/bin"
        PATH = "${POETRY_HOME}:${PATH}"
    }

    stages {
        stage('Check Poetry') {
            steps {
                sh 'which poetry'
                sh 'poetry --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'poetry install'
            }
        }

        stage('Restart Service') {
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

