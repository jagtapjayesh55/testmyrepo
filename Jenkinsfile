pipeline {
    agent any

    stages {
        stage('Check Files') {
            steps {
                sh 'ls -l'
            }
        }

        stage('Run Application') {
            steps {
                sh 'python3 main.py'
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                python3 -m pip install --user pytest
                export PATH=$HOME/.local/bin:$PATH
                pytest
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Tests passed. Build is GOOD."
        }
        failure {
            echo "❌ Tests failed. Build is BLOCKED."
        }
    }
}

