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
    }
}
