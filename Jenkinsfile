pipeline {
    agent any
  
    environment {
        APP_NAME = 'FlaskApp'
        CONTACT_EMAIL = 'lissy.asha@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Setting up virtual environment & installing dependencies...'
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh '''
                    . venv/bin/activate
                    pytest tests/
                '''
            }
        }

        stage('Deploy (staging)') {
            steps {
                echo 'Deploying Flask app using Gunicorn...'
                sh '''
                    pkill gunicorn || true
                    . venv/bin/activate
                    gunicorn -w 4 -b 0.0.0.0:5000 app:app &
                '''
            }
        }
    }

    post {
        success {
            mail to: "${CONTACT_EMAIL}",
                 subject: "${APP_NAME} ✅ SUCCESS: ${env.JOB_NAME} Build #${env.BUILD_NUMBER}",
                 body: "The Flask application was built and deployed successfully."
        }
        failure {
            mail to: "${CONTACT_EMAIL}",
                 subject: "${APP_NAME} ❌ FAILURE: ${env.JOB_NAME} Build #${env.BUILD_NUMBER}",
                 body: "The build or test failed. Check the Jenkins logs."
        }
    }
}
