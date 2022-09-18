pipeline {
    agent any 
    
    environment {
        JAVA_VERSION="11"
        DEVOPS_BATCH="AUG2022"
    }
  
    tools {
        jdk 'jdk11'
        maven 'maven386'
    }

    stages {
        stage('Checkout') {
            steps{
                checkout scm
            }
        }

        stage('Compile') {
            steps{
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps{
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps{
                sh 'mvn package'
                sh 'echo $DEVOPS_BATCH'
                sh 'echo one more'
            }
        }
    }
   


}