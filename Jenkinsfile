
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Installing dependencies'
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests'
                bat 'python -m unittest discover -s . -p "test_*.py"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Flask application'

                bat '''
                    if not exist deployment mkdir deployment
                    copy /Y app.py deployment\\app.py
                    copy /Y requirements.txt deployment\\requirements.txt
                '''
            }
        }
    }
}
