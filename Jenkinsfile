pipeline {
        agent none
        tools {nodejs "Node20"}
        stages {
          stage("build & SonarQube analysis") {
            agent any
            steps {
              withSonarQubeEnv('SonarQube') {
                sh 'npx sonarqube-scanner -Dsonar.projectKey=simpleNode2'
              }
            }
          }
          stage("Quality Gate") {
            steps {
              timeout(time: 120, unit: 'SECONDS') {
                waitForQualityGate abortPipeline: true
              }
            }
          }
        }
      }
