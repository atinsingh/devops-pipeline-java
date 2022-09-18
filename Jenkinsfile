pipeline {
    agent any 
    
    environment {
        JAVA_VERSION=11
        DEVOPS_BATCH=AUG2022
    }
    parameters {
         choice(name: 'DEPLOYMENT_ENV', 
         choices: ['UAT1', 'UAT2', 'PRERPOD'], 
         description: 'Select Env for deploy'
         )
         string(name: 'DUMMYSTR',
         description:'Just a dummy value', 
         defaultValue:'Atin')
    }
    triggers {
         pollSCM('* * * * *') 
    }

    options {
         buildDiscarder logRotator(artifactDaysToKeepStr: '2', artifactNumToKeepStr: '2', daysToKeepStr: '', numToKeepStr: '3')
         quietPeriod 5
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
    }
    post {
        always {
            slackSend channel: 'devops', message: 'BUILD COMPLETED'
        }
    }


}