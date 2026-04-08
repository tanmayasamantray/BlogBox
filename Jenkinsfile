pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/tanmayasamantray/BlogBox.git'
            }
        }

        stage('Install Backend Dependencies') {
            steps {
                dir('backend') {
                    sh 'npm install'
                }
            }
        }

        stage('Run Backend') {
            steps {
                dir('backend') {
                    sh 'nohup node server.js &'
                }
            }
        }
    }
}