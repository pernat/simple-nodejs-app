node {
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
    withNPM() {
    sh 'cd app/ && npm install'
    }

  }
}
