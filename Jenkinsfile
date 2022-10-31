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
                    this is pending genersted to jenkins.. video time 57.00 https://youtu.be/Yk7k3yEguQA pic 18
                }
            }
        }
        stage('Docker Image Build') {

            steps{

                script {
                    sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID'
                    sh 'docker image tag $JOB_NAME:v1.$BUILD_ID suresh394/$JOB_NAME:v1.$BUILD_ID'
                    sh 'docker image tag $JOB_NAME:v1.$BUILD_ID suresh394/$JOB_NAME:latest'
                }
            }
        }
        stage('push image to the dockerHUB') {

            steps{

                script{

                    wirhCredentials([string(credentialsId: 'git_creds', variable: 'docker_hub_cred')]){

                        sh 'docker login -u suresh394 -p ${docker_hub_cred}'
                        sh 'docker image push suresh394/$JOB_NAME:v1.$BUILD_ID'
                        sh 'docker image push suresh394/$JOB_NAME:latest' 
                    }

                }
            }
        }





    }
}