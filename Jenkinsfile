pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'g++ -o PES1UG20CS622 PES1UG20CS622.cpp'
                sh 'jenkins-cli.jar -s http://localhost:8080/ build PES1UG20CS622-1'
            }
        }

        stage('Test') {
            steps {
                sh './PES1UG20CS622'
            }
        }

        stage('Deploy') {
            steps {
                sh 'make deploy'
            }
        }
    }

    post {
        always {
            catchError {
                echo 'Pipeline succeeded!'
            }
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
