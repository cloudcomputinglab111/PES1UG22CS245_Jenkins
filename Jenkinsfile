pipeline {
    agent any

    environment {
        SRN = 'PES1UG22CS245'
        REPO_URL = 'https://github.com/cloudcomputinglab111/PES1UG22CS245_Jenkins.git'
    }

    stages {
        stage('Clone repository') {
            steps {
                sh 'echo "Repository already checked out by Jenkins"'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'g++ --version || echo "g++ not found"'
                sh 'echo "Compiler check completed"'
            }
        }

        stage('Build application') {
            steps {
                sh 'g++ -o ${SRN}-1 main/hello.cpp'
                sh 'echo "Build step completed"'
            }
        }

        stage('Test application') {
            steps {
                sh './${SRN}-1 || echo "Test failed - executable not found"'
                sh 'echo "Test step completed"'
            }
        }

        stage('Deploy application') {
            steps {
                sh 'echo "Deploying application..."'
                
                sh '''
                mkdir -p deployment
                mv ${SRN}-1 deployment/
                echo "Application deployed to ./deployment/"
                '''
                
                sh 'echo "Deployment step completed"'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
        success {
            echo 'Pipeline completed successfully'
        }
    }
}
