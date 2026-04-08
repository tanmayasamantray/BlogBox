pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo "Using default SCM checkout"
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
                    sh '''
                    pkill node || true
                    nohup node server.js > app.log 2>&1 < /dev/null &
                    '''
                }
            }
        }
    }
}