pipeline {
    agent any
    environment {
        APP_ENV = 'production'
    }
    parameters {
        choice(name: 'ENV', choices: ['dev', 'stage', 'prod'], description: 'Select Environment')
        string(name: 'TAG', defaultValue: 'v1.0', description: 'Enter Version Tag')
    }
    stages {
        stage('Build') {
            steps {
                echo "Building for ${env.APP_ENV} with Tag: ${params.TAG}"
            }
        }
        stage('Deploy to Production') {
            when {
                expression { params.ENV == 'prod' }
            }
            steps {
                echo "Deploying to Production Server..."
            }
        }
    }
    post {
        always {
            echo "Cleaning up workspace (Always runs)..."
        }
        success {
            echo "Pipeline executed SUCCESSFULLY!"
        }
        failure {
            echo "Pipeline FAILED!"
        }
    }
}
