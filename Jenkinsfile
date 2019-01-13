pipeline {
  agent any
  stages {
    
    stage('Build') {
      steps{
        bat 'F:\\2CS_SIL_S7\\Outils\\gradle-4.10.2\\bin\\gradle build'
      } 
      post {
                  failure {
                    mail(subject: 'echec du build', body: 'les derniers changements ont échoué le build', from: 'ey_al_houcine@esi.dz', to: 'fm_bara@esi.dz')
                  }
                 success {

                    mail(subject: 'build success', body: 'build avec success des derniers changements', from: 'ey_al_houcine@esi.dz', to: 'fm_bara@esi.dz')
                  }
             }
      }
      
    
    
    stage('Code analysis') {
      parallel {
         stage('SonarQube analysis') {
                    steps {
                      script {
                          scannerHome = tool 'SonarQube Scanner 3.2.0.1227'
                      }
                      withSonarQubeEnv('sonarqube') {
                        bat 'F:\2CS_SIL_S7\Outils\TP3\sonar-scanner-3.2.0.1227-windows\bin\sonar-scanner'
                      }
                        waitForQualityGate abortPipeline: true
                    }
                  }
        stage('Test Reporting') {
              steps {
                jacoco(maximumBranchCoverage: '60')
              }
            }
        }
    }
  }
}
