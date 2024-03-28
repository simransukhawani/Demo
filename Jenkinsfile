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
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Run Bandit') {
            steps {
                sh 'bandit -r .'
            }
        }
        
        stage('Run Tests') {
            steps {
                sh 'python -m unittest discover'
            }
        }
    }
}
