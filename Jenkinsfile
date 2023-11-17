pipeline {
    agent any

    options {
        timeout(time: 1, unit: 'HOURS')
        buildDiscarder(logRotator(numToKeepStr: '10'))
        disableConcurrentBuilds()
    }

    stages {
        stage('Preparation') {
            steps {
                checkout scm
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
