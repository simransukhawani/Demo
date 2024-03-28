pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/simransukhawani/Demo.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                script {
                    sh 'pip install -r requirements.txt'
                }
            }
        }
        
        // Add more stages for testing, linting, etc.
    }
    
    // Add post actions if needed
}
