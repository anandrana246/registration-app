pipeline{
    agent any
    tools{
        maven 'M398'
    }

    stages{
        stage("Cleanup Workspace"){
            steps{
                cleanWs()
            }
        }
        stage("Checkout Code"){
            steps{
                checkout scm
            }    
        }    

        stage("Build Application"){
            steps{
                sh "mvn clean package"
            }
        }
        stage("Test"){
            steps{
                sh "mvn test"
            }    
        }
        stage("Printing Parameters"){
            steps{
                sh "echo the environmet is ${params.ENVIRONMENT}"
                sh "echo sleep_time ${params.SLEEP}"
                sh "sleep ${params.SLEEP}"
                sh "echo the the branch is ${params.BRANCH}"
            }
        }
    }
}
