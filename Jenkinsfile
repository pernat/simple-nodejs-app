pipeline {
    agent any
    tools {nodejs "Node20"}

    stages {

    stage('SCM') {
        steps {
        checkout scm
        }
    }
    stage('SonarQube Analysis') {
        steps {
        def scannerHome = tool 'SonarQube';
        withSonarQubeEnv('SonarQube') {
        sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=simpleNode2"
        }
        }
    }
    stage('Build') {
        steps {
        withNPM(npmrcConfig: '7bcf87c3-9d83-4617-b92d-c582d94deaac') {
        sh 'cd app/ && npm install'
        }
}
    }

}
}
