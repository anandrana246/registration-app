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

        stage("Build Application"){
            steps{
                sh "mvn clean package"
            }
        }
    }
}