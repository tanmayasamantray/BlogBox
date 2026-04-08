pipeline {
    agent any

    tools {
        sonarRunner 'sonar-scanner'
    }

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

        stage('SonarQube Analysis') {
            steps {
                dir('backend') {
                    withSonarQubeEnv('sonarqube') {
                        sh '''
                        sonar-scanner \
                        -Dsonar.projectKey=blog-backend \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://3.108.199.223:9000
                        '''
                    }
                }
            }
        }
        stage('Run Backend') {
            steps {
                dir('backend') {
                    sh '''
                    pkill node || true
                    setsid node server.js > app.log 2>&1 < /dev/null &
                    '''
                }
            }
        }
    }
}