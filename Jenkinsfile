pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the GitHub repository
                git branch: 'main', url: 'https://github.com/simransukhawani/Demo.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Install Python dependencies from requirements.txt
                script {
                    try {
                        sh 'pip install -r requirements.txt'
                    } catch (Exception e) {
                        echo "Failed to install dependencies: ${e.message}"
                        error "Failed to install dependencies"
                    }
                }
            }
        }
        
        stage('Run Bandit') {
            steps {
                // Run Bandit for security checks
                script {
                    try {
                        sh 'bandit -r .'
                    } catch (Exception e) {
                        echo "Failed to run Bandit: ${e.message}"
                        error "Failed to run Bandit"
                    }
                }
            }
        }
        
        stage('Run Tests') {
            steps {
                // Run Python unit tests
                script {
                    try {
                        sh 'python -m unittest discover'
                    } catch (Exception e) {
                        echo "Failed to run tests: ${e.message}"
                        error "Failed to run tests"
                    }
                }
            }
        }
    }
    
    post {
        always {
            // Print the average stage times
            echo "Average stage times:"
            script {
                def times = currentBuild.rawBuild.getActions(hudson.model.Cause$UserIdCause.class)[0]?.getThreadName()
                for (def entry : times) {
                    echo "${entry.key}: ${entry.value}"
                }
            }
        }
    }
}
