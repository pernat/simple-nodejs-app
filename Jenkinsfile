node {
  tools {nodejs "Node20"}
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarQube';
    withSonarQubeEnv('SonarQube') {
      sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=simpleNode2"
    }
  }
  stage('Build') {
    withNPM(npmrcConfig: '7bcf87c3-9d83-4617-b92d-c582d94deaac') {
    sh 'cd app/ && npm install'
    }

  }
}
