pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'F:\\2CS_SIL_S7\\Outils\\gradle-4.10.2\\bin\\gradle build'
      }
      post {
              failure {
                mail(subject: 'Repported changes', body: 'Salam, some changes occured and the build failed', from: 'ey_al_houcine@esi.dz', to: 'fm_bara@esi.dz')
              }
             success {

                mail(subject: 'Repported changes', body: 'Salam, some changes occured and the build successeded', from: 'ey_al_houcine@esi.dz', to: 'fm_bara@esi.dz')
              }
         }
    }
  }
}
