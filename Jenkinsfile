pipeline {
    agent any

    tools {
        maven 'M398'  // Using Maven tool configuration
    }

    environment {
        REPO = 'https://github.com/anandrana246/registration-app.git'
    }

    parameters {
        choice(name: 'BRANCH', choices: ['main', 'test'], description: 'Branch on which pipeline executes')
        choice(name: 'ENVIRONMENT', choices: ['Prod', 'Dev', 'Test'], description: 'Environment for Pipeline')
        string(name: 'SLEEP', defaultValue: '10', description: 'Sleep duration in seconds')
    }

    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()  // Cleans workspace before execution
            }
        }

        stage('Git Checkout') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: "${params.BRANCH}"]],
                    userRemoteConfigs: [[url: "${REPO}"]]
                ])
            }
        }

        stage('Build Application') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Printing Parameters') {
            steps {
                echo "The environment is ${params.ENVIRONMENT}"
                echo "Sleep time is ${params.SLEEP}"
                sh "sleep ${params.SLEEP}" // Ensure sleep command runs properly
                echo "The branch is ${params.BRANCH}"
            }
        }
    }
}
