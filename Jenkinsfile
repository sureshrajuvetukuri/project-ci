pipeline {

    agent any

    stages {

        stage('Git Checkout'){

            steps{
                git branch: 'main', url: https://github.com/sureshrajuvetukuri/project-ci.git
            }
        }
        stage('UNIT Testing'){

            steps{
                sh 'mvn test'
            }
        }
        stage('Interation testing'){

            steps{
                sh 'mvn verify -DskipUnitTest'
            }
        }
        stage('Maven Build'){

            steps{
                sh 'mvn clean install'
            }
        }

    
    }
}