pipeline {
    agent any

    environment {
        PYTHON_VERSION = '3.8'
        VIRTUAL_ENV = "/var/lib/jenkins/python-env"
    }

    options {
        timeout(time: 1, unit: 'HOURS')
        buildDiscarder(logRotator(numToKeepStr: '10'))
        disableConcurrentBuilds()
    }

    stages {
        stage('Preparation') {
            steps {
                script {
                    sh "python${PYTHON_VERSION} -m venv ${VIRTUAL_ENV}"
                    sh "source ${VIRTUAL_ENV}/bin/activate"
                    sh "python${PYTHON_VERSION} -m pip install -r requirements.txt"
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run tests using the unittest module
                    sh "python${PYTHON_VERSION} -m unittest test_calculator.py"
                }
            }
        }

        stage('Deployment') {
            steps {
                script {
                    // Add implementation steps here if necessary
                    echo 'Script implementation...'
                }
            }
        }
    }

    post {
        always {
            echo 'Finishing the pipeline'
            sh "deactivate"
        }

        success {
            echo 'The pipeline was successful. You can perform additional actions here.'
        }

        failure {
            echo 'The pipeline has failed. You can perform error handling actions here.'
        }
    }
}
