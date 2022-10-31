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
        stage('Maven Build') {

            steps{
                sh 'mvn clean install'
            }
        }
        stage('Static code analysis') {
            steps {
                scripts{
                    withsonarQubeEnv(credentialsId: 'sonar-api')
                    sh 'mvn clean package sonar:sonar'

                }
                
            }
        }
        stage('Quality Gate status'){

            steps{
                
                script{

                    waitForQualityGate abortPipeline: false, credentialsId: 'sonar-api'
                }
            }
        }
        stage('upload war file to nexus'){

            steps{

                script{
                    this is pending genersted to jenkins.. video time 57.00 https://youtu.be/Yk7k3yEguQA
                }
            }
        }
        


    }
}